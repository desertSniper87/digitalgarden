---
{"dg-publish":true,"permalink":"/scapy-vlan-scripting/"}
---

Got it — I can help you **passively enumerate VLAN info** by sniffing Cisco Discovery Protocol (CDP) and VLAN Trunking Protocol (VTP) traffic and by observing [[802.1Q\|802.1Q]] tags on the wire. I won’t provide VLAN-hopping (attack) code, but here’s a safe, **authorization-only** tool you can run to discover:
- VTP Management Domain (from CDP TLV and VTP summary ads)
- Native VLAN (from CDP TLV)
- All VLAN IDs seen in live traffic (from 802.1Q tags)
- A heads-up if Dynamic Trunking Protocol (DTP) frames are present (often a misconfiguration risk)
    

  

### **Usage**

```bash
# 1) Python 3.9+ recommended
pip install scapy

# 2) Run as root/admin to capture packets
sudo python vlan_enum_sniffer.py -i eth0
```

### **Python script:** 

### **vlan_enum_sniffer.py**

```python
#!/usr/bin/env python3
import argparse
import signal
import sys
from collections import defaultdict
from datetime import datetime

from scapy.all import sniff, Ether, Dot1Q, LLC, SNAP, Raw

# Cisco OUI used in SNAP for CDP/VTP/DTP
CISCO_OUI = 0x00000C
PID_CDP   = 0x2000
PID_VTP   = 0x2003
PID_DTP   = 0x2004

state = {
    "vtp_domain": None,          # last seen VTP domain (from CDP or VTP)
    "native_vlan": None,         # last seen Native VLAN (from CDP)
    "cdp_from": set(),           # (device_id, port_id) pairs, if we parse them
    "seen_vlans": set(),         # VLAN IDs observed from 802.1Q tags
    "saw_dtp": False,            # whether DTP frames have been observed
    "vtp_versions": set(),       # VTP versions observed (1/2/3)
    "events": []                 # simple event log
}

def log(msg):
    ts = datetime.now().strftime("%H:%M:%S")
    print(f"[{ts}] {msg}")
    state["events"].append(f"[{ts}] {msg}")

def parse_cdp_tlvs(payload: bytes):
    """
    CDP payload starts: 1B version, 1B TTL, 2B checksum, then TLVs:
    TLV: 2B type, 2B length (incl header), value...
    We only parse what we need (VTP domain TLV=0x0009, Native VLAN TLV=0x000A).
    Optionally device-id (0x0001) and port-id (0x0003) for context.
    """
    if len(payload) < 4:
        return {}

    tlvs = {}
    # Skip CDP header (v, ttl, cksum)
    i = 4
    while i + 4 <= len(payload):
        t = int.from_bytes(payload[i:i+2], 'big')
        l = int.from_bytes(payload[i+2:i+4], 'big')
        if l < 4 or i + l > len(payload):
            break
        v = payload[i+4:i+l]
        if t not in tlvs:
            tlvs[t] = []
        tlvs[t].append(v)
        i += l
    return tlvs

def handle_cdp(pkt):
    # CDP is LLC/SNAP with Cisco OUI, PID 0x2000
    snap = pkt[SNAP]
    raw_bytes = bytes(snap.payload) if snap.payload is not None else b""
    tlvs = parse_cdp_tlvs(raw_bytes)

    # Device ID (0x0001) and Port ID (0x0003) are handy context
    dev = None
    port = None
    if 0x0001 in tlvs:
        try:
            dev = tlvs[0x0001][0].decode(errors="ignore")
        except Exception:
            pass
    if 0x0003 in tlvs:
        try:
            port = tlvs[0x0003][0].decode(errors="ignore")
        except Exception:
            pass
    if dev or port:
        state["cdp_from"].add((dev or "?", port or "?"))

    # VTP Management Domain (0x0009)
    if 0x0009 in tlvs and tlvs[0x0009]:
        try:
            vtp_dom = tlvs[0x0009][0].decode(errors="ignore").strip("\x00")
            if vtp_dom and vtp_dom != state["vtp_domain"]:
                state["vtp_domain"] = vtp_dom
                log(f"CDP: VTP Management Domain = '{vtp_dom}'"
                    + (f" (from {dev}/{port})" if (dev or port) else ""))
        except Exception:
            pass

    # Native VLAN (0x000A) — 2-byte integer
    if 0x000A in tlvs and tlvs[0x000A]:
        try:
            nv = int.from_bytes(tlvs[0x000A][0][:2], 'big')
            if nv and nv != state["native_vlan"]:
                state["native_vlan"] = nv
                log(f"CDP: Native VLAN = {nv}"
                    + (f" (from {dev}/{port})" if (dev or port) else ""))
        except Exception:
            pass

def handle_vtp(pkt):
    """
    VTP (SNAP PID 0x2003). We’ll minimally parse the header for Version and Domain Name.
    VTP Summary Advertisement (Code=0x01) format (simplified):
      [0]=Version, [1]=Code, [2]=Followers, [3]=DomainLen, [4:4+N]=Domain
    We only need Version and Domain for enumeration.
    """
    raw = bytes(pkt[SNAP].payload) if pkt[SNAP].payload is not None else b""
    if len(raw) < 4:
        return
    version = raw[0]
    code = raw[1]
    dlen = raw[3]
    dom = ""
    if 4 + dlen <= len(raw) and dlen > 0:
        try:
            dom = raw[4:4+dlen].decode(errors="ignore").strip("\x00")
        except Exception:
            pass

    if version in (1, 2, 3):
        if version not in state["vtp_versions"]:
            state["vtp_versions"].add(version)
            log(f"VTP: Observed VTP version {version}")

    if dom and dom != state["vtp_domain"]:
        state["vtp_domain"] = dom
        log(f"VTP: Domain = '{dom}' (Code=0x{code:02x})")

def handle_dtp(pkt):
    # Presence of DTP frames can indicate ports negotiating trunks (often undesirable)
    if not state["saw_dtp"]:
        state["saw_dtp"] = True
        log("DTP: Detected Dynamic Trunking Protocol frames on the wire (review switchport configs).")

def collect_vlan_tags(pkt):
    # Extract all 802.1Q VLAN IDs (handles stacked Dot1Q, e.g., QinQ)
    layer = pkt
    found = []
    while layer:
        if layer.haslayer(Dot1Q):
            q = layer.getlayer(Dot1Q)
            if q is not None:
                vlan = int(getattr(q, 'vlan', 0))
                if vlan:
                    found.append(vlan)
            layer = q.payload if q is not None else None
        else:
            break
    for v in found:
        if v not in state["seen_vlans"]:
            state["seen_vlans"].add(v)
            log(f"802.1Q: Observed VLAN ID {v}")

def is_cisco_snap(pkt):
    if not pkt.haslayer(LLC) or not pkt.haslayer(SNAP):
        return False
    llc = pkt[LLC]
    snap = pkt[SNAP]
    return (llc.dsap == 0xAA and llc.ssap == 0xAA and llc.ctrl == 0x03
            and getattr(snap, "OUI", None) == CISCO_OUI)

def packet_handler(pkt):
    try:
        # Collect 802.1Q VLAN tags from any packets
        if pkt.haslayer(Dot1Q):
            collect_vlan_tags(pkt)

        # Handle Cisco SNAP protocols (CDP/VTP/DTP)
        if is_cisco_snap(pkt):
            pid = getattr(pkt[SNAP], "code", None)
            if pid == PID_CDP:
                handle_cdp(pkt)
            elif pid == PID_VTP:
                handle_vtp(pkt)
            elif pid == PID_DTP:
                handle_dtp(pkt)
    except Exception as e:
        log(f"Error parsing packet: {e}")

def print_summary():
    print("\n========== VLAN Enumeration Summary ==========")
    if state["vtp_domain"]:
        print(f"VTP Domain        : {state['vtp_domain']}")
    else:
        print("VTP Domain        : (not observed)")
    if state["native_vlan"]:
        print(f"Native VLAN (CDP) : {state['native_vlan']}")
    else:
        print("Native VLAN (CDP) : (not observed)")
    if state["vtp_versions"]:
        print(f"VTP Versions      : {', '.join(str(v) for v in sorted(state['vtp_versions']))}")
    else:
        print("VTP Versions      : (not observed)")
    if state["seen_vlans"]:
        print(f"VLAN IDs Observed : {', '.join(str(v) for v in sorted(state['seen_vlans']))}")
    else:
        print("VLAN IDs Observed : (none yet)")

    print(f"DTP Present       : {'yes' if state['saw_dtp'] else 'no'}")
    if state["cdp_from"]:
        print("CDP Neighbors     :")
        for dev, port in sorted(state["cdp_from"]):
            print(f"  - {dev} / {port}")
    print("==============================================\n")

def main():
    parser = argparse.ArgumentParser(
        description="Passive VLAN enumerator: sniff CDP/VTP and 802.1Q tags (authorization required)."
    )
    parser.add_argument("-i", "--iface", required=True, help="Interface to sniff (e.g., eth0)")
    parser.add_argument("-f", "--filter", default="",
                        help="Optional BPF filter (default: none; you may use 'ether proto 0x8100' or 'ether dst 01:00:0c:cc:cc:cc')")
    parser.add_argument("-c", "--count", type=int, default=0,
                        help="Stop after N packets (0 = run until Ctrl+C)")
    parser.add_argument("-t", "--timeout", type=int, default=0,
                        help="Stop after T seconds (0 = no timeout)")
    args = parser.parse_args()

    def handle_sigint(sig, frame):
        print_summary()
        sys.exit(0)

    signal.signal(signal.SIGINT, handle_sigint)

    log(f"Sniffing on {args.iface} (count={args.count or '∞'}, timeout={args.timeout or '∞'})...")
    if args.filter:
        log(f"Using BPF filter: {args.filter}")

    # Hints:
    # - CDP/VTP/DTP often hit multicast 01:00:0c:cc:cc:cc
    # - Trunk links are where VTP advertisements travel; access ports may not see them
    sniff(
        iface=args.iface,
        prn=packet_handler,
        store=False,
        count=args.count,
        timeout=args.timeout,
        filter=args.filter if args.filter else None
    )
    print_summary()

if __name__ == "__main__":
    main()
```


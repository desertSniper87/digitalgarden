---
{"dg-publish":true,"permalink":"/firewalking/"}
---

Firewalking is a method of collecting information about remote networks behind firewalls.
- It is a technique that uses [[Time to Live\|TTL]] values to determine gateway ACL filters and map networks by analyzing the IP packet response.
- It probes ACLs on packet filtering routers/firewalls using the same method as tracerouting.
- Firewalking involves sending TCP or UDP packets into the firewall where the TTL value is one hop greater than the targeted firewall.
- If the packet makes it through the gateway, the system forwards it to the next hop, where the TTL equals one, and prompts an ICMP error message at the point of rejection with a "TTL exceeded in transit" message.
- This method helps locate a firewall; additional probing facilitates fingerprinting and identification of vulnerabilities.
- The detailed information obtained from firewalking can also assist attackers in crafting more precise and stealthy attack strategies, potentially aiding IDS evasion.
- Understanding firewall rules can help attackers avoid detection using allowed ports and protocols, thereby reducing the likelihood of triggering IDS alerts.
- Firewalk is a well-known application used for firewalking.
- It has two phases: a network discovery phase and a scanning phase.
- It comes with various open-source Linux distributions.
- [[net/sec/tools/nmap\|nmap]] has a firewalk script that can be used to perform firewalking.
- Firewalk and Nmap firewalk scripts provide critical insights into network configurations and firewall rules that can be leveraged to bypass security measures, including IDS, when combined with other evasion techniques.


```mermaid
graph TD
    A[Attacker] --> B[Phase 1: Network Discovery]
    B --> C[Send TTL packets to discover hops]
    C --> D{Response received?}
    D -->|ICMP TTL Exceeded| E[Hop discovered - increment TTL]
    D -->|No response| F[Dead end or filtered]
    E --> G[Continue until firewall found]
    F --> G
    G --> H[Firewall Location Identified]
    
    H --> I[Phase 2: Scanning Phase]
    I --> J[Set TTL = Firewall_hops + 1]
    J --> K[Send probes to various ports]
    
    K --> L{Packet filtered by firewall?}
    L -->|Allowed through| M[Receive ICMP TTL Exceeded<br/>from next hop]
    L -->|Blocked by firewall| N[No response or<br/>ICMP unreachable]
    
    M --> O[Port/Protocol ALLOWED<br/>through firewall]
    N --> P[Port/Protocol BLOCKED<br/>by firewall]
    
    O --> Q[Map allowed services]
    P --> Q
    Q --> R[Repeat for all target ports]
    R --> S[Complete ACL Map]
    
    S --> T[Intelligence Gathering Complete]
    T --> U[Plan Attack Strategy]
    U --> V[Use allowed ports for stealth]
    V --> W[Bypass IDS using<br/>legitimate protocols]
    
    %% Styling
    classDef phase fill:#e1f5fe
    classDef discovery fill:#f3e5f5
    classDef scanning fill:#e8f5e8
    classDef result fill:#fff3e0
    classDef attack fill:#ffebee
    
    class B,I phase
    class C,D,E,F,G,H discovery
    class J,K,L,M,N,O,P,Q,R,S scanning
    class T,U,V,W attack
    
    %% Network topology subgraph
    subgraph NET[Network Topology]
        AT[Attacker<br/>TTL=4] 
        R1[Router 1<br/>Hop 1] 
        R2[Router 2<br/>Hop 2]
        FW[Firewall<br/>Hop 3]
        TGT[Target Network<br/>Hop 4]
        
        AT -.->|TTL=4| R1
        R1 -.->|TTL=3| R2  
        R2 -.->|TTL=2| FW
        FW -.->|TTL=1| TGT
        TGT -.->|ICMP TTL Exceeded| AT
    end
    
    %% Example results subgraph
    subgraph RES[Firewalking Results]
        PORT80[Port 80 HTTP<br/>✅ ALLOWED]
        PORT443[Port 443 HTTPS<br/>✅ ALLOWED]
        PORT22[Port 22 SSH<br/>❌ BLOCKED]
        PORT23[Port 23 Telnet<br/>❌ BLOCKED]
        PORT53[Port 53 DNS<br/>✅ ALLOWED]
    end
```
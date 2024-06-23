---
{"dg-publish":true,"permalink":"/fixing-haproxy-keepalived-vip-race-condition/"}
---

To ensure both HAProxy instances are running, even if they do not have the floating IP, you need to configure HAProxy to bind to the virtual IP in a non-strict manner. Here are a few solutions to address your problem:

### Solution 1: Configure HAProxy to Bind Non-Strictly

You can configure HAProxy to bind to the VIP even if it is not yet assigned to the interface. This can be done by setting `transparent` and `interface` options in HAProxy configuration.

Update your HAProxy configuration to include the `transparent` and `interface` options:

```c
frontend http_front
    bind 172.22.21.36:80 transparent interface ens18
    ...
```

This will allow HAProxy to bind to the IP without it being present on the interface initially.

### Solution 2: Dummy Interface with VIP

Create a dummy interface that always holds the VIP, ensuring HAProxy can start without issues. This interface will be overridden by keepalived when it assigns the VIP.

1. **Create a dummy interface**:

   Add a dummy interface configuration on both nodes (e.g., `ens19`) and assign the VIP to it.

   On Debian-based systems, you can add the following to `/etc/network/interfaces`:

```c
   auto dummy0
   iface dummy0 inet static
       address 172.22.21.36
       netmask 255.255.255.0
       pre-up ip link add dummy0 type dummy
       post-down ip link del dummy0
```

   On Red Hat-based systems, create a file `/etc/sysconfig/network-scripts/ifcfg-dummy0` with:

```c
   DEVICE=dummy0
   IPADDR=172.22.21.36
   NETMASK=255.255.255.0
   ONBOOT=yes
```

And then enable the dummy interface:

```c 
ip link add dummy0 type dummy
ip addr add 172.22.21.36/24 dev dummy0
ip link set dummy0 up
```

2. **Ensure the dummy interface is up** on boot:

```bash
 systemctl restart networking
```

### Solution 3: Modify Keepalived to Start HAProxy

Ensure `haproxy` starts regardless of the VIP being present. You can modify your `keepalived` configuration to start `haproxy` if it's not running when the VIP is assigned.

1. **Add start script for HAProxy**:

   Add a script to start `haproxy` if it's not running. Place the script at `/usr/local/bin/start_haproxy.sh`:

   ```bash
   #!/bin/bash

   if ! pgrep haproxy > /dev/null; then
       systemctl start haproxy
   fi
   ```

   Make sure the script is executable:

   ```bash
   chmod +x /usr/local/bin/start_haproxy.sh
   ```

2. **Modify keepalived configuration**:

   Update the `notify_master` and `notify_backup` sections to ensure `haproxy` starts as needed:

```c
   vrrp_instance VI_01 {
       ...
       notify_master "/usr/local/bin/start_haproxy.sh && /usr/bin/echo 'Master Active' > /tmp/keepalived.state"
       notify_backup "/usr/local/bin/start_haproxy.sh && /usr/bin/echo 'Backup Active' > /tmp/keepalived.state"
       notify_fault "/usr/bin/echo 'Master-Backup Fault' > /tmp/keepalived.state"
   }
   ```

### Summary

- **Non-strict binding**: Adjust HAProxy configuration to bind in a transparent manner.
- **Dummy interface**: Create a dummy interface holding the VIP to ensure HAProxy can start.
- **HAProxy start script**: Ensure HAProxy starts regardless of VIP presence by modifying the keepalived configuration.

Choose the method that best fits your setup and preferences. The non-strict binding approach is often the simplest to implement.

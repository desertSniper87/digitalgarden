---
{"dg-publish":true,"permalink":"/metasploit-pivoting/"}
---

pivoting in penetration testing can be done using Metasploit, where an attacker uses a compromised host (with a Meterpreter session) as a pivot point to access other systems within a private network.

## Explanation of Setting Up Routing Rules in Metasploit:

When an attacker gains access to a machine inside the target network (via a Meterpreter session), that machine becomes a **pivot point**. The attacker needs to route network traffic through this compromised machine to access other systems on the internal network that are not directly accessible from the attacker’s machine. This technique is commonly called pivoting.

### Steps Involved:

1. Background the Meterpreter Session:
   - After compromising a system and getting a Meterpreter session, the first step is to background the session, which means pausing it so that you can issue commands for network routing.

```msfconsole
background
```

2. Add a Route:
   - You use the route add command in Metasploit to set up a routing rule. This tells Metasploit to send any traffic destined for a specific IP range (subnet) through the compromised machine (the system you have the Meterpreter session on).

   - The command structure is:

```
route add <target_ip_address> <subnet_mask> <session_number>
```

- <target_ip_address>: The IP address (or range) you want to route traffic to (e.g., 10.10.10.0).
- <subnet_mask>: The subnet mask for the target network (e.g., 255.255.255.0).

- <session_number>: The session number corresponding to the Meterpreter session you established earlier (e.g., 1 for session number 1).

Example:

Suppose an attacker wants to route all traffic destined for the 10.10.10.0/24 network (the private network) through a Meterpreter session (session number 1). The command would be:

```
route add 10.10.10.0 255.255.255.0 1
```

- This command tells Metasploit to route all network traffic destined for IP addresses within the range 10.10.10.0/24 to session number 1, i.e., the compromised machine, which acts as the gateway to the internal network.

## Why Set Up Routing Rules?

- Accessing Private Networks: Attackers may not have direct access to internal systems from their attacker machine. However, by using a compromised system as a pivot point, they can route traffic through that system to reach other devices on the internal network that are otherwise inaccessible.

- Lateral Movement: This technique is part of lateral movement, where an attacker moves from one compromised system to another within the target network.

- Metasploit’s Role: In Metasploit, setting up routing rules allows the attacker to use the Meterpreter session to forward network traffic to other systems. Metasploit automatically sets up the required networking configurations to make this possible.

## Visualizing Pivoting and Routing:

Here’s a simple example:

- Attacker Machine (External): 192.168.1.100
- Compromised Host (Pivot Point): 10.0.0.5 (System with Meterpreter session)
- Target Network (Private Network): 10.10.10.0/24

Once the attacker sets up the route to the private network via the compromised host, any traffic destined for the 10.10.10.0/24 network from Metasploit will automatically be routed through 10.0.0.5.

### Key Points to Remember:

- Pivoting requires a valid session on an internal machine, typically through Meterpreter.
- Routing rules are essential for telling Metasploit which network traffic should be routed through the compromised system.
- The route add command is used to configure these rules.
- Once the route is added, the attacker can scan ports and exploit vulnerabilities on other machines within the private network.

### Example Workflow:

1. Compromise a system inside the target network (with Metasploit, for example).
2. Background the Meterpreter session.
3. Set up a routing rule to direct traffic to the internal network via the compromised system.
4. Perform network actions (e.g., port scanning, vulnerability scanning) on other systems in the internal network.
5. Exploit any vulnerable systems inside the private network.

### Clean Up:

After completing the actions, it’s important to remove the routing rules to avoid detection:

```
route delete <target_ip_address> <subnet_mask>
```

---

### Summary:

To set up routing rules in Metasploit for pivoting:

1. Establish a Meterpreter session with a compromised host.
2. Use route add \<IP address> \<subnet mask> \<session number> to route traffic to the target private network.
3. This allows you to scan ports and exploit services within the private network through the compromised system.
   This setup is critical for lateral movement and network reconnaissance in penetration testing.

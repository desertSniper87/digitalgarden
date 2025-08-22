---
{"dg-publish":true,"permalink":"/ghostwriting-sh/"}
---

## **Ghostwriting Malware Bypass Technique**


- Ghostwriting is a **bypass technique** that involves modifying **the structure of the malware code** without affecting its functionality.
- This can be done by deconstructing the assembly code and adding arbitrary code.

- Attackers use this technique to **bypass endpoint device security** agents such as [[antivirus\|antivirus]] software and hide malware to evade signature-based detection.
## **Ghostwriting.sh**


Attackers use tools such as **Ghostwriting.sh** to modify the malware structure.

Ghostwriting works by:
- Binary deconstruction
- Insertion of arbitrary assembly code
- Reconstruction

It uses built-in [[net/sec/tools/metasploit\|metasploit]] tools to perform these actions. **Ghostwriting.sh** automates this process.

  

## **Example Scenario**

Run the following commands to execute the Ghostwriting.sh script:
```
# Change directory to where the Ghostwriting.sh script is loaded
cd /opt/ghostwriting/

# Execute the script with sudo privileges
sudo ./ghostwriting.sh
```

### **What the script does**

- Downloads and installs missing dependencies
- Creates a MeterPreter reverse TCP binary file to connect to the machine’s private IP address
- Disassembles the executable and inserts junk code for signature evasion
- Reassembles the binary code with the junk code
- Opens a web server on the machine’s IP address to facilitate file transfer to the victim machine
  

This helps attackers avoid endpoint security systems.

---

## **Output Example**

```
****************************************************
Opening webserver on <IP_Address>:8000 for file transfer
Ctrl+C to continue after file transfer
****************************************************
Serving HTTP on 0.0.0.0 port 8000 ...
```

---

Do you want me to also add **syntax highlighting for assembly snippets** (like junk code insertion), so it looks even cleaner for a cybersecurity report or training doc?
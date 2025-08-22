---
{"dg-publish":true,"permalink":"/application-whitelisting-and-dll-hijacking/"}
---


**Application whitelisting** is a security feature in Windows systems to defend against insecure or malicious application execution. It contains the list of signed applications that are allowed to run in the system. 

### Execution of Signed Applications

When executing a **legitimate and signed application, Windows looks for the required DLLs in the current location where the executable is saved and then searches in other locations.**

### [[DLL Hijacking\|DLL Hijacking]]

Attackers perform **DLL hijacking** by placing a malicious DLL with a legitimate name that the application is looking for in the same directory where the executable resides. The malicious DLL gets executed along with the application, potentially disabling endpoint security.

### Exploiting DLL Handling

In DLL hijacking, attackers abuse the process of handling DLLs by Windows OS along with its search order, which helps in locating DLLs during their loading into a program. This method of hijacking DLL loads allows attackers to:

- Maintain persistence
- Elevate privileges
- Avoid detection during malicious DLL loading

### Avoiding Detection

Attackers can use tools like **rundll32.exe**, **[[regsvr32\|regsvr32]].exe**, and **PowerShell** to load malicious DLLs and bypass endpoint security solutions. For example, an attacker can execute the following command to execute a malicious DLL using **regsvr32.exe**:

```bash
regsvr32 /s /n /u /i:malicious.dll
```
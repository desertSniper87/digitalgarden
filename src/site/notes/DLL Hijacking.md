---
{"dg-publish":true,"permalink":"/dll-hijacking/"}
---

## Privilege Escalation Using DLL Hijacking

- Most Windows applications do not use the **fully qualified path** when loading an external DLL library
  - They first search the directory from which they have been loaded
  - If attackers can place a malicious DLL in the application directory
    - The application will execute the malicious DLL in place of the real DLL
- An application program “.exe” may need library.dll (usually in the Windows system directory) to install the application
  - In case of the application failing to specify the library.dll path Windows will search for the DLL in the directory from which the application was launched
- If an attacker has already placed the DLL in the same directory as program.exe
  - then that malicious DLL will load instead of the real DLL
  - which allows the attacker to gain remote access to the target system.

## Tools

- [[Spartacus (DLL Hijacker)\|Spartacus (DLL Hijacker)]]

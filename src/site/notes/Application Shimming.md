---
{"dg-publish":true,"permalink":"/application-shimming/"}
---

**[Матрица MITRE ATT&CK](https://mitre.ptsecurity.com/en-US/T1546.011?utm_source=chatgpt.com)

**Application shimming** is a technique used to modify the behavior of applications at runtime without changing the application’s original code. It is typically used to add compatibility or fix bugs in legacy software. In the context of security, it can also be used for malicious purposes, such as executing unauthorized code when an application runs.

## How Application Shimming Works:

- **Shim DLLs**: A shim is a small library that intercepts system calls or API calls made by an application and modifies the behavior of the application. The shim DLL is loaded before the legitimate DLL or executable, allowing the shim to “shim” or modify the original behavior.
- **Compatibility Layer**: Shims are often used to ensure that older applications continue to work on newer versions of the operating system. For example, a shim can be used to make a legacy application behave as though it’s running on an older operating system version that it was designed for.
- **Malicious Shimming**: Attackers can use shimming to inject malicious code into the target application. By modifying the behavior of a legitimate application, an attacker could redirect network traffic, steal credentials, or install other malware.

- Shims are applied using the sdbinst.exe utility, which registers a shim database on the system.
- Once registered, the shim database can modify the behavior of applications by redirecting API calls or injecting DLLs.
- Attackers can create custom shim databases to execute malicious payloads when specific applications are launched.()

Shims run in user mode, and they cannot modify the kernel. Some of these shims can be used to bypass UAC (RedirectEXE), inject malicious DLLs (InjectDLL), capture memory addresses (GetProcAddress), etc. An attacker can use these shims to perform different attacks including disabling Windows Defender, privilege escalation, installing backdoors, etc.
## Example:

- A user installs an older version of a program that doesn’t run properly on a newer version of Windows. The system can apply a shim to make the program think it’s running in a compatible environment, allowing it to function correctly without modifying the program itself.

**Real-World Exploitation**:

- Threat groups like FIN7 have used application shimming to achieve persistence by injecting malicious code into critical system processes like services.exe.
- These malicious shims can bypass User Account Control ([[User Account Control\|UAC]]), disable security features, or inject backdoors into running processes.
## Defending Against Application Shimming:

- **Shim Database Management**: Windows has a **Shim Database** (called **AppCompat**), which stores and manages shim configurations. Administrators can control and restrict the use of shims on their systems.
- **Code Signing**: Ensure that all software, including shims, is properly signed. This prevents unauthorized shims from being loaded into applications.
- **Group Policies**: Restrict the use of shims through system or application-specific group policies to ensure they are only applied to trusted applications.

## VS [[Path Interception\|Path Interception]]

- **Path Interception**:
  - Involves manipulating the PATH variable to redirect the execution of commands or programs to malicious files.
  - Used in attacks like **DLL hijacking**.

- **Application Shimming**:
  - Involves creating a layer between the application and system calls to alter application behavior.
  - Can be used for compatibility or malicious purposes, such as injecting code into the target application.

Both techniques are powerful but can be dangerous in malicious hands. Understanding and mitigating these vulnerabilities is key to maintaining system security.

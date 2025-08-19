---
{"dg-publish":true,"permalink":"/rootkit/"}
---

A collection of software tools that enable unauthorized users to gain control of a system without being detected. Rootkits are typically used to hide the presence of other malicious software or to maintain privileged access.

The term “rootkit” comes from “root” (the highest level of administrative access in Unix-like operating systems) and “kit” (a set of tools or software).


1. *Hardware/Firmware Rootkit*
	- **Location**: Embedded in hardware components like the [[BIOS\|BIOS]], [[Unified Extensible Firmware Interface\|UEFI]] firmware, or peripheral devices.
	- **Functionality**: They can manipulate how the hardware interacts with the OS, providing ==control over processes before the operating system fully loads==, and allowing attackers to execute arbitrary code in the early boot process.
	- **Persistence**: Highly persistent; can survive OS reinstallation and hard drive formatting. ￼
	- **Detection**: Extremely difficult to detect with standard security tools. Specialized hardware inspection is often required. ￼
	- **Example**: The “[[LoJax\|LoJax]]” UEFI rootkit, used by the Fancy Bear hacking group, modified the UEFI firmware to maintain persistent access to infected systems.  ￼


2. *Library-Level Rootkit*
	- **Location**: Operates within shared **System libraries** or [[Dynamic Link Library\|Dynamic Link Libraries]] (DLLs).
	- **Functionality**: ==Intercepts **system calls** or API functions to alter the behavior of applications without modifying the applications themselves==.
	- **Detection**: Can be detected by monitoring system call behaviors and comparing them against known good baselines.
	- **Example**: A rootkit that replaces standard system libraries with malicious versions to log keystrokes or capture sensitive data.


3. *Hypervisor-Level Rootkit*
	- **Location**: Installs beneath the operating system, within the hypervisor layer that manages virtual machines. ￼
	- **Functionality**: Controls the guest operating system by intercepting and modifying its operations, often without detection. ￼
	- **Detection**: Difficult to detect; requires specialized tools that can analyze hypervisor behavior and interactions with guest systems.
	- **Example**: The “Blue Pill” rootkit, a theoretical example, demonstrated how a hypervisor could be used to hide a malicious guest OS from the host system.  ￼

    > Attackers create hypervisor-level rootkits by exploiting hardware features such as [[Intel VT\|Intel VT]] and [[AMD-V\|AMD-V]]. These rootkits run in Ring-1 and host the OS of the target machine as a virtual machine, thereby intercepting all hardware calls made by the target OS. This kind of rootkit works by modifying the system’s boot sequence so that it is loaded instead of the original virtual machine monitor.

4. *Boot-Loader-Level Rootkit* ([[Bootkit\|Bootkit]])
	- **Location**: Resides in the boot sector, such as the Master Boot Record (MBR) or Volume Boot Record (VBR). ￼
	- **Functionality**: Loads before the operating system, allowing it to gain control early in the **boot process** and potentially bypass security mechanisms.
	- **Detection**: Can be detected by inspecting the boot sector for unauthorized modifications.
	- **Example**: The “Stoned Bootkit,” one of the earliest known bootkits, modified the MBR to gain control over the system during startup.  ￼


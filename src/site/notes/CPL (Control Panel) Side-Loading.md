---
{"dg-publish":true,"permalink":"/cpl-control-panel-side-loading/"}
---

**CPL files** are generally developed for Windows control panels to organize and provide quick access to different tools in the Control Panel, making it easier to manage these tools.
- However, attackers can exploit CPL files to evade detection systems through legitimate`. cpl` files, which are typically associated with Windows Control Panel applets.
- This technique is also known as **CPL sideloading**, which mimics the functionality of the original CPL applet and helps malicious activities become benign to both users and security systems.
-

### How CPL Sideloading Works

When a user executes a legitimate CPL file, malicious code embedded within the file is loaded.
- This can be achieved through various methods such as executing a specific function within the CPL file or exploiting vulnerabilities in how Windows handles CPL files.
- Attackers then trick Windows to load the CPL file through another legitimate application or process instead of directly executing the CPL file.
- For example, a trusted application configuration file can be manipulated to load a CPL file during the initialization process.

Because CPL files are not typically associated with malware, traditional detection systems may overlook them during routine scans.
- In addition, attackers may configure the system to ensure that the malicious CPL file is executed each time the system boots up or at specific intervals, thereby allowing them to maintain persistent access to the compromised system.

### Common Techniques Used by Attackers

- **Renaming Harmful Files**: Attackers may rename harmful `.dll` files with `.cpl` extensions and register them at a specific location in the Windows registry. Even if these DLLs do not follow the rules for CPL files and do not have certain functions, they can still be loaded and run through the `DllEntryPoint` when the control panel is opened.

- **CPLResourceRunner**: Attackers can also use tools like **CPLResourceRunner** to create malicious CPL files. The following steps outline how attackers might use this tool:

  1. **Generate Payload**: Use **Cobalt Strike** to generate a fully staged payload in x86 format, saving it as `beacon.bin`.
  2. **Convert to Shellcode**: Execute `ConvertShellcode.py` on `beacon.bin` to convert it into shellcode saved as `shellcode.txt`.
  3. **Encode Shellcode**: Run the following command to encode the contents of `shellcode.txt` into Base64 format and prepare it for inclusion in a resource file:
     ```bash
     cat shellcode.txt |sed ‘s/[, ]//g; s/0x//g;’ |tr -d ‘\n’ |xxd -p -r |gzip -c |base64 > b64shellcode.txt
     ```
  4. **Copy Encoded Content**: Copy the encoded content from `b64shellcode.txt` to the `Resources.txt` file in the same folder.
  5. **Create Malicious CPL**: Collect the resources in x86 format and copy the `CPLResourceRunner.dll` into a new file named `maliciousnew.cpl`.

Thus, CPL sideloading can be used as a sophisticated evasion technique, where attackers leverage trusted system components to conceal malicious activities and evade traditional detection mechanisms.


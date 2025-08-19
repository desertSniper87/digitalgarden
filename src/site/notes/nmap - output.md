---
{"dg-publish":true,"permalink":"/nmap-output/"}
---



You can save the output of an `nmap` scan to a file using the `-o` options. Here's how you do it:

1. **To save as a text file**:
   ```bash
   nmap -oN output.txt <target>
   ```

2. **To save in XML format**:
   ```bash
   nmap -oX output.xml <target>
   ```

3. **To save in a grepable format**:
   ```bash
   nmap -oG output.gnmap <target>
   ```

4. **To save in all formats**:
   ```bash
   nmap -oA output <target>
   ```

This will generate three files:
- `output.nmap` (normal text)
- `output.xml` (XML)
- `output.gnmap` (grepable format)
---
{"dg-publish":true,"permalink":"/heap-spraying/"}
---

- https://en.wikipedia.org/wiki/Heap_spraying
- [Understanding Heap SprayingAttacks](https://www.linkedin.com/pulse/understanding-heap-sprayingattacks-luis-soares-m-sc-/)
- [What Is Heap Spraying? How It Works & Examples \| Twingate](https://www.twingate.com/blog/glossary/heap%20spraying?utm_source=chatgpt.com)
- [Heap spraying definition – Glossary \| NordVPN](https://nordvpn.com/cybersecurity/glossary/heap-spraying/?utm_source=chatgpt.com)

**Heap spraying** is a memory corruption exploit technique used to facilitate arbitrary code execution. It involves allocating large blocks of memory on the heap and filling them with specific byte sequences, often including malicious shellcode. This increases the likelihood that an attacker can redirect the program’s execution flow to the injected code, thereby compromising the system.
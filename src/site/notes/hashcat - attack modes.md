---
{"dg-publish":true,"permalink":"/hashcat-attack-modes/"}
---

Hashcat has **five main attack modes**, each suited to different cracking strategies:

---

### `-a 0` — **Straight Mode**

Applies wordlists **as-is** (optionally with rules).

```bash
hashcat -a 0 hashes.txt wordlist.txt
```

---

### `-a 1` — **Combinator Attack**

Combines words from two dictionaries.

```bash
hashcat -a 1 hashes.txt dict1.txt dict2.txt
```

---

### `-a 3` — **Brute-force (Mask) Attack**

Tests all combinations defined by a **mask**.

```bash
hashcat -a 3 hashes.txt ?l?l?l?l?d?d
```

---

### `-a 6` — **Hybrid Wordlist + Mask**

Appends a mask to each word in a wordlist.

```bash
hashcat -a 6 hashes.txt wordlist.txt ?d?d
```

---

### `-a 7` — **Hybrid Mask + Wordlist**

Prepends a mask to each word in a wordlist.

```bash
hashcat -a 7 hashes.txt ?d?d wordlist.txt
```

---

🧠 **Tip**: Combine `-a 0` with `--rules` for powerful transformations like leetspeak, suffixing numbers, etc.

Let me know your use case and I’ll suggest the most effective mode.
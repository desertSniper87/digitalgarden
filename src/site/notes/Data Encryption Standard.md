---
{"dg-publish":true,"permalink":"/data-encryption-standard/"}
---

- **Outdated**
- Key length: 56 bits

- DES is a [[Symmetric Encryption\|Symmetric-Key Block Cipher]]
- DES's encryption works as a combination of the following:
	- [[One-Time Pad\|One-Time Pad]]
	- [[Permutation Cipher\|Permutation Cipher]]
	- substitution ciphers applied to bit sequences
- It uses the `same key` in both `encrypting and decrypting` data.


- The key consists of `64 bits`
- The actual key length of DES is only `56 bits`
- `8 bits` used as a checksum (Error correction)
- Each 64-bit block of plaintext is encrypted to a 64-bit block of ciphertext (To prevent the danger from [[Frequency Analysis\|Frequency Analysis]])


## 3DES

- Key Size: 56 bit

- An extension of DES is the so-called [Triple DES / 3DES](https://en.wikipedia.org/wiki/Triple_DES)
- The procedure for 3DES usually consists of three keys
	- The **first** key being used to **encrypt** the data
	- The **second** to **decrypt** the data
	- The **third** to **encrypt** the data again.
- provides higher security using longer key lengths and is now the most widely used symmetric encryption technology.
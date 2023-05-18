---
{"dg-publish":true,"permalink":"/apple/ios/troubleshooting/repairing-po-ds-in-ios/"}
---

---
alias: [pod reset]
---

```bash
cd ios && pod deintegrate && pod install --repo-update && cd ..
```

If it fails, delete `podfile.lock`
---
{"dg-publish":true,"permalink":"/apple/ios/troubleshooting/repairing-po-ds-in-ios/"}
---



```bash
cd ios && pod deintegrate && pod install --repo-update --verbose && cd ..
```

If it fails, delete `podfile.lock`


```bash
cd ios && rm Podfile.lock && pod deintegrate && pod install --repo-update --verbose && cd ..
```
---
{"dg-publish":true,"permalink":"/apple/ios/troubleshooting/repairing-po-ds-in-ios/"}
---



```bash
cd ios && pod deintegrate && pod install --repo-update --verbose && cd ..
```

Combined with npm reset

```bash
rm -rf package-lock.json && rm -rf yarn.lock && rm -rf node_modules  
rm -rf ios/Podfile.lock && rm -rf ios/Pods  
yarn install  
cd ios && pod deintegrate && pod install --repo-update --verbose && cd ..
```

If it fails, delete `podfile.lock`


```bash
cd ios && rm Podfile.lock && pod deintegrate && pod install --repo-update --verbose && cd ..
```

Combined with npm reset

```bash
rm -rf package-lock.json && rm -rf yarn.lock && rm -rf node_modules  
rm -rf ios/Podfile.lock && rm -rf ios/Pods  
yarn install  
cd ios && rm Podfile.lock && pod deintegrate && pod install --repo-update --verbose && cd ..
```
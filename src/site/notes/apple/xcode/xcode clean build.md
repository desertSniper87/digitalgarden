---
{"dg-publish":true,"permalink":"/apple/xcode/xcode-clean-build/"}
---


## Removing derived data

```bash
rm -rf ~/Library/Developer/Xcode/DerivedData
```
## Removing Saved State

```bash
rm -rf ~/Library/Saved Application State/com.apple.dt.Xcode.savedState/
```

## Removing Everything

```bash
rm -rf ~/Library/Developer
rm -rf ~/Library/Developer/Caches/com.apple.dt.Xcode
rm -rf ~/Library/Developer/Saved Application State/com.apple.dt.Xcode.savedState
rm -rf ~/Dev/ekyc-native-app/ios/QuickPass.xcodeproj/project.xcworkspace/xcuserdata
```

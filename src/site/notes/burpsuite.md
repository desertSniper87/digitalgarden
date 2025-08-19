---
{"dg-publish":true,"permalink":"/burpsuite/"}
---

## Importing certificate in [[firefox\|firefox]]


```cardlink
url: https://portswigger.net/burp/documentation/desktop/external-browser-config/certificate/ca-cert-firefox
title: "Installing Burp's CA certificate in Firefox"
description: "Before attempting to install Burp's CA certificate, make sure that you have successfully confirmed that the proxy listener is active and have configured ..."
host: portswigger.net
favicon: /content/images/logos/favicon.ico
image: https://portswigger.net/content/images/logos/burpsuite-twittercard.png
```
1. http://burpsuite/
2. Authorities > Import


## Usage in [[apple/mac\|macos]] and [[firefox\|firefox]]

Use https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/


## Download

- https://portswigger.net/burp/releases/professional-community-2021-12

## Using burploader in [[apple m1\|apple m1]]

```bash
cd ~/dev/Burp\ Suite/
"/opt/homebrew/Cellar/openjdk/24.0.1/libexec/openjdk.jdk/Contents/Home/bin/java" "--add-opens=java.desktop/javax.swing=ALL-UNNAMED" "--add-opens=java.base/java.lang=ALL-UNNAMED" "--add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED" "--add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED" "--add-opens=java.base/jdk.internal.org.objectweb.asm.Opcodes=ALL-UNNAMED" "-javaagent:burploader.jar" "-noverify" "-jar" "/Applications/Burp Suite Professional.app/Contents/Resources/app/burpsuite_pro.jar"
```

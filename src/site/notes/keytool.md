---
{"dg-publish":true,"permalink":"/keytool/"}
---


## Links

1. [[Keystore\|Keystore]] (Importing file into keystore)
2. [[FIxing Old Certificate Chain\|Keytool - import certificate]]
3. [[keytool - import jks into truststore\|keytool - import jks into truststore]]

## Convert PKCS#12 file

### Example 1

```bash
keytool -importkeystore \
 -srckeystore @sharif2008__quick-pass-keystore.bak.p12\
 -srcstoretype pkcs12\
 -srcalias quickpass\
 -destkeystore quickpass.jks\
 -deststoretype jSUB CA Certificates 2016ks\
 -deststorepass 123456\
 -destalias quickpass
```

### Example 2

```bash
keytool -importkeystore -srckeystore server.p12 -srcstoretype PKCS12 -destkeystore server.jks -deststoretype JKS
```

## Reference

### P12 to JKS

1. [How to convert p12 keystore to jks keystore](https://www.ibm.com/support/pages/how-convert-p12-keystore-jks-keystore)
2. [security - Need help converting P12 certificate into JKS - Stack Overflow](https://stackoverflow.com/questions/16244182/need-help-converting-p12-certificate-into-jks)


```bash
keytool -importkeystore -srckeystore [MY_FILE.p12] -srcstoretype pkcs12
 -srcalias [ALIAS_SRC] -destkeystore [MY_KEYSTORE.jks]
 -deststoretype jks -deststorepass [PASSWORD_JKS] -destalias [ALIAS_DEST]
```
## Converting [[cer\|cer]] to [[jks\|jks]]

```bash
keytool -importcert -file "client-ca.cer" -keystore truststore.jks -alias "bcc-ca-client"
```

## Change Alias

```bash
keytool -keyclone -alias "bcc-ca-client" -dest "bcc-class-2-sub-ca-g2"  -keystore  ./keystore.jks -storepass 123456
```

## jks to p12

```bash
keytool \
  -importkeystore \
  -srckeystore server.jks \
  -destkeystore server.p12 \
  -srcstoretype JKS \
  -deststoretype PKCS12 \
  -srcstorepass 123456 \
  -deststorepass 123456 \
  -noprompt

```


## View JKS files


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">






- [[jks\|jks]]

[The Most Common Java Keytool Keystore Commands](https://www.sslshopper.com/article-most-common-java-keytool-keystore-commands.html)

```bash
keytool -list -v -keystore server.jks
```


</div></div>

## PFX to JKS

```bash
keytool -importkeystore -srckeystore server.pfx -srcstoretype pkcs12 -srcalias 1 -srcstorepass 123456 -destkeystore server.jks -deststoretype jks -deststorepass 123456 -destalias 1
```
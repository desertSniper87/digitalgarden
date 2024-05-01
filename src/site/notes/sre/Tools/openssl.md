---
dg-publish: true
alias: [key to pem, pfx to p7b, pfx to crt]
---

## Docs

- [OpenSSL C Docs](https://commondatastorage.googleapis.com/chromium-boringssl-docs/rsa.h.html)

## Links

1. [[OpenSSL - Calculating Digest Value\|OpenSSL - Calculating Digest Value]]
2. [[OpenSSL - Generating PSK\|OpenSSL - Generating PSK]]
3. [[OpenSSL - Installation\|OpenSSL - Installation]]
4. [[OpenSSL - Generate CSR for SSL Certificate\|OpenSSL - Generate CSR for SSL Certificate]]


## Flags

| Flag            | Description                   |
| --------------- | ----------------------------- |
| `-new`, `-X509` | Generates self signed root CA |
| `-subj`         | CA Identity                   |
| `-des3`         | [Triple DES](https://en.wikipedia.org/wiki/Triple_DES)                              |

## Generation of [[net/sec/x509\|x509]] certificates

- [/docs/man1.0.2/man1/x509.html](https://www.openssl.org/docs/man1.0.2/man1/x509.html)


## View certificate information

```bash
openssl x509 \
  --in server.crt \
  -text \
  --noout
```


### View p7b chain


```bash
openssl pkcs7 -in yourfile.p7b -print_certs -noout
```

### [[net/sec/PKI/PEM\|PEM]] file 

```bash
openssl x509 -in server.pem -noout -text
```

## Converting to PEM file from CRT and KEY

```bash
openssl x509 -inform DER -outform PEM -in server.crt -out server.crt.pem
```

```bash
cat server.crt server.key > server.includesprivatekey.pem
```

## Debugging

```bash
openssl s_client -connect localhost:8081
```

## Reference

1. [How to create a .pem file for SSL Certificate Installations | Support | SUSE](https://www.suse.com/support/kb/doc/?id=000018152)

### Generating Fullchain certificate 

[OpenSSL create certificate chain with Root & Intermediate CA | GoLinuxCloud](https://www.golinuxcloud.com/openssl-create-certificate-chain-linux/)


## Private key to pem


```bash
openssl rsa -in server.key -text > privatekey.pem
```


## P12/PFX to P7B

```bash
openssl pkcs12 -in yourfile.pfx -out yourfile.pem -nodes
```

```bash
openssl crl2pkcs7 -nocrl -certfile yourfile.pem -out yourfile.p7b
```


## P12/PFX to CRT

```bash
openssl pkcs12 -in $PFX -clcerts -nokeys -out $CRT
```

## CER to CRT

- [Do I need to convert .CER to .CRT for Apache SSL certificates? If so, how? - Stack Overflow](https://stackoverflow.com/a/37252887/7154462)

```bash
openssl x509 -inform DER -in subca_class_2.cer -out subca_class_2.crt
```

## Installation in [[forums/ios\|forums/ios]]

- [ios - Installing OpenSSL library for Xcode - Stack Overflow](https://stackoverflow.com/questions/22692564/installing-openssl-library-for-xcode)
- [Easy inclusion of OpenSSL into iOS projects](https://atastypixel.com/easy-inclusion-of-openssl-into-iphone-app-projects/)


## Reading public keys

### Format wars

- https://stackoverflow.com/questions/7818117/why-i-cant-read-openssl-generated-rsa-pub-key-with-pem-read-rsapublickey

## [[apple/xcode/xcode\|xcode]] linker flags


```bash
-lcrypto
```

```bash
-L/opt/homebrew/opt/openssl@1.1/lib
```


### Build Settings > Search Path

```bash
/opt/homebrew/opt/openssl@1.1/include/openssl
```

## Create PFX from CRT and Key

```bash
openssl pkcs12 -export -out tls.pfx -inkey tls.key -in tls.crt
```



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



```bash
openssl x509 -outform der -in cert.pem -out tls.cer
```

```bash
openssl x509 -inform der -in tls.cer -out tls.crt
```

(From [Here](https://serverfault.com/questions/992700/convert-der-cer-format-to-base64-cer))

</div></div>


## Concat full chain 


https://gist.github.com/singhabhinav/132b8196abac026b43fa
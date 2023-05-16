---
{"dg-publish":true,"alias":["key to pem","pfx to p7b"],"permalink":"/sre/tools/openssl/","dgPassFrontmatter":true}
---


## Links

1. [[OpenSSL - Calculating Digest Value\|OpenSSL - Calculating Digest Value]]
2. [[OpenSSL - Generating PSK\|OpenSSL - Generating PSK]]


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


## Installation in [[forums/ios\|ios]]

- [ios - Installing OpenSSL library for Xcode - Stack Overflow](https://stackoverflow.com/questions/22692564/installing-openssl-library-for-xcode)
- [Easy inclusion of OpenSSL into iOS projects](https://atastypixel.com/easy-inclusion-of-openssl-into-iphone-app-projects/)
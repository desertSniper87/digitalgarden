---
{"dg-publish":true,"permalink":"/sre/tools/openssl/"}
---


## Links


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
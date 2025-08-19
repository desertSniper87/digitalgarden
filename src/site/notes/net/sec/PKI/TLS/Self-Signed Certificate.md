---
{"dg-publish":true,"permalink":"/net/sec/pki/tls/self-signed-certificate/"}
---


## Creating a self signed certificate using [[sre/Tools/openssl\|openssl]]

```bash
openssl genrsa -out key.pem 2048
```


```bash
openssl req -new -sha256 -key key.pem -out csr.csr
```


```bash
openssl req -x509 -sha256 -days 365 -key key.pem -in csr.csr -out cert.pem
```


```bash
openssl pkcs12 -export -out cert.pfx -inkey key.pem -in cert.pem
```



## Standalone Script

```bash
openssl genrsa -out server.key 2048
openssl req -new -sha256 -key server.key -out server.csr \
    -subj "/C=BD/ST=Dhaka/L=Dhaka/O=Bangladesh Computer Council/OU=Certificate Authority/CN=flask-bcc.gov.bd/emailAddress=support@bcc-ca.gov.bd"
openssl req -x509 -sha256 -days 365 -key server.key -in server.csr -out server.crt
openssl pkcs12 -export -out cert.pfx -inkey server.key -in server.crt -password 123456
```


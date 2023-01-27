---
{"dg-publish":true,"permalink":"/net/sec/pki/tls/implementation-of-m-tls-in-node-js/"}
---


## References

2. [[net/sec/PKI/TLS/TLS Client Authentication|TLS Client Authentication]]
3. [[nodejs|nodejs]]


## Step 1 - Generate certifcate autority using [[sre/Tools/openssl|openssl]]


### Generate CA certificate

Here, Common name is BCC

```bash
openssl req \
  -new \
  -x509 \
  -nodes \
  -newkey rsa:2048\
  -days 365 \
  -subj '/CN=bcc' \
  -keyout ca.key \
  -out ca.crt
```


### Generate Server Certificate

#### Generate Server Key

```bash
openssl genrsa \
  -out server.key 2048
```

### Generate CSR

Here common name is localhost

```bash
openssl req \
  -new \
  -key server.key \
  -subj '/CN=localhost' \
  -out server.csr
```

### Generate Signed Certificate

```bash
openssl x509 \
  -req \
  -in server.csr \
  -CA ca.crt \
  -CAkey ca.key \
  -CAcreateserial \
  -days 365 \
  -out server.crt
```

### Generate Client Certificate


#### Generate Client Key

```bash
openssl genrsa \
  -out client.key 2048
```

### Generate CSR

Here common name is client's name

```bash
openssl req \
  -new \
  -key client.key \
  -subj '/CN=torsho' \
  -out client.csr
```

### Generate Signed Certificate

```bash
openssl x509 \
  -req \
  -in client.csr \
  -CA ca.crt \
  -CAkey ca.key \
  -CAcreateserial \
  -days 365 \
  -out client.crt
```

Then we can convert [[net/sec/PKI/TLS/p12|crt to p12]]

## Testing the server

```bash
curl \
  --cacert ca.crt \
  --key client.key \
  --cert client.crt \
  https://localhost:3000
```
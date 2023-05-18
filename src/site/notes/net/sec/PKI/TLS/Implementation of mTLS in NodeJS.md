---
{"dg-publish":true,"permalink":"/net/sec/pki/tls/implementation-of-m-tls-in-node-js/"}
---


## References

2. [[net/sec/PKI/TLS/TLS Client Authentication\|TLS Client Authentication]]
3. [[nodejs\|nodejs]]
4. [[sre/Tools/openssl\|openssl]]


## Step 1 - Generate certifcate autority using [[sre/Tools/openssl\|openssl]]

### Ext File (v3.ext)

```yaml

authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[alt_names]
DNS.1 = bcc-ca-website.org


```


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

#### Generate CA certificate for client

```bash
openssl req \
  -new \
  -x509 \
  -nodes \
  -newkey rsa:2048\
  -days 365 \
  -subj '/CN=bcc-client' \
  -keyout ca-client.key \
  -out ca-client.crt
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
  -subj '/CN=bcc-ca-website.org' \
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
  -extfile v3.ext \
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
  -CA ca-client.crt \
  -CAkey ca-client.key \
  -CAcreateserial \
  -days 365 \
  -out client.crt
```

Then, 
1. we can convert [[net/sec/PKI/TLS/p12\|crt to p12]]
2. import ca/client certificate into keystore using [[Keystore#Add certificate into keystore \| keystore]]

## Testing the server

```bash
curl \
  --cacert ca.crt \
  --key client.key \
  --cert client.crt \
  https://localhost:3000
```
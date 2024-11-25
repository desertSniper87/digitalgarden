---
{"dg-publish":true,"permalink":"/net/sec/pki/tls/"}
---


- Transport Layer Security 
- [Wikipedia](https://en.wikipedia.org/wiki/Transport_Layer_Security)
- Successor protocol to [[net/sec/PKI/TLS\|SSL]]


At the heart of TLS is Public Key Infrastructure ([[net/sec/PKI\|PKI]]) and in particular [[net/sec/x509\|X.509]] certificates.

## Definition

- https://www.cloudflare.com/en-gb/learning/ssl/transport-layer-security-tls/

![](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3wZIhjRIjfVSmCbVqkBKzb/4a7aa34324108c725dc25fc9e7c4ea4a/tls-ssl-handshake.png )

## Links

1. [[sre/Tools/openssl\|openssl]]
2. [[Debugging SSL\|Debugging SSL]]
3. [[java/spring/Debugging SSL in Spring\|Debugging SSL in Spring]]

## TLS CA certificates

> Certificates are data structures that include a public key, a digital signature, and some other data. Clients use certificates to authenticate servers during TLS handshakes.

## Issues

### CA certificate key too weak

#### References

- [curl - SSL CA Certificates](https://curl.haxx.se/docs/sslcerts.html)


## Links

1. [[net/sec/PKI/TLS/TLS Client Authentication\|TLS Client Authentication]]




## Tools

- [sslshopper](https://www.sslshopper.com/ssl-checker.html)
- [Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html)
## Docs

- https://carrickbartle.com/certificates.html
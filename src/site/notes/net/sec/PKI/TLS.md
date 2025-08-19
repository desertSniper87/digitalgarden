---
{"dg-publish":true,"permalink":"/net/sec/pki/tls/"}
---


- Transport Layer Security 
- [Wikipedia](https://en.wikipedia.org/wiki/Transport_Layer_Security)
- Successor protocol to [[net/sec/PKI/TLS\|SSL]]


At the heart of TLS is Public Key Infrastructure ([[net/sec/PKI\|PKI]]) and in particular [[net/sec/x509\|X.509]] certificates.

## Definition

- https://www.cloudflare.com/en-gb/learning/ssl/transport-layer-security-tls/

![|531x303](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3wZIhjRIjfVSmCbVqkBKzb/4a7aa34324108c725dc25fc9e7c4ea4a/tls-ssl-handshake.png)

### TLS Handshake

> TLS is still using [[net/protocols/Transmission Control Protocol\|TCP]] as its **transport protocol**, so we will still see acknowledgment packets from the stream coming over port 443.

1. Client and server exchange hello messages to agree on connection parameters.
2. Client and server exchange necessary cryptographic parameters to establish a premaster secret.
3. Client and server will exchange x.509 certificates and cryptographic information allowing for authentication within the session.
4. Generate a master secret from the premaster secret and exchanged random values.
5. Client and server issue negotiated security parameters to the record layer portion of the TLS protocol.
6. Client and server verify that their peer has calculated the same security parameters and that the handshake occurred without tampering by an attacker.

![image-1-14.webp|787x289](/img/user/image-1-14.webp)

- We can see that the client establishes a session to the server using port 443 `boxed in blue`:
	- This signals the server that it wishes to use HTTPS as the application communication protocol.

- Once a session is initiated via TCP:
	- A TLS ClientHello is sent next to begin the TLS handshake
- During the handshake several parameters are agreed upon:
	- Session identifier
	- Peer x509 certificate
	- Compression algorithm to be used
	- The cipher spec encryption algorithm
	- Session resumability
	- A 48-byte master secret shared between the client and server to validate the session.

- Once the session is established:
	- All data and methods will be sent through the TLS connection and appear as TLS Application Data `as seen in the red box`

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

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">





- [sslshopper](https://www.sslshopper.com/ssl-checker.html)
- [Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html)

</div></div>

## Docs

- https://carrickbartle.com/certificates.html
---
{"dg-publish":true,"permalink":"/enabling-ssl/tls-in-keycloak/"}
---

## Enabling SSL/TLS in Keycloak

### Using tls crt and key
Keycloak can be configured to load the required certificate infrastructure using files in PEM format or from a Java Keystore. When both alternatives are configured, the PEM files takes precedence over the Java Keystores.

```bash
           ./kc.sh start --hostname=keycloak-poc\
                         --http-port=80\
                         --proxy reencrypt\
                         --https-certificate-file=/root/certs/tls.crt \
                         --https-certificate-key-file=/root/certs/tls.key\
                         > keycloak.stdout 2>&1 & echo "$!" > keycloak.pid
```

### Using java Keystore

From [[#Tutorials]] / https://www.keycloak.org/server/enabletls:  

> When no keystore file is explicitly configured, but `http-enabled` is set to false, Keycloak looks for a `conf/server.keystore` file.
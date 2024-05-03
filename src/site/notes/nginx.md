---
{"dg-publish":true,"permalink":"/nginx/"}
---


## Links

1. [[nginx/nginx as a load balancer\|nginx/nginx as a load balancer]]
2. [[nginx stream\|nginx stream]]
3. [[nginx - serve static websites\|nginx - serve static websites]]
4. [[nginx - run php\|nginx - run php]]
5. [[nginx - ssl-tls config\|nginx - ssl-tls config]]

## Check nginx config

```bash
nginx -t
```
## Installation

### [[os/Linux/ubuntu\|ubuntu]]

```bash
sudo apt install nginx
```

## Running with [[sre/docker/docker\|docker]]

```
docker run -it --rm -d -p 8080:80 --name web nginx
```

```bash
docker run -it --rm -d -p 8080:80 --name web -v /root/test_webroot:/usr/share/nginx/html nginx
```


## Using [[sre/Tools/openssl\|openssl]] to generate self signed certificate

### Reference 

1. [How To Create a Self-Signed SSL Certificate for Nginx in Ubuntu 16.04 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-in-ubuntu-16-04)


## SSL Passthrough for [[java/Spring Boot\|Spring Boot]]

### Reference 

1. [java - Unable to SSL Pass through Ingress Nginx Controller - Stack Overflow](https://stackoverflow.com/questions/66196561/unable-to-ssl-pass-through-ingress-nginx-controller)


## Redirection

- https://stackoverflow.com/questions/26587354/how-to-implement-nginx-case-insensitive-directory-location-redirection-301
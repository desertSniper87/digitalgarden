---
{"dg-publish":true,"permalink":"/java/tomcat-server/"}
---

[Github](https://github.com/apache/tomcat)

---
- [[Tomcat Logging\|Tomcat Logging]]
- [[java/tomcat - exploits\|tomcat - exploits]]
# Embedded Tomcat

- [[Running embedded tomcat on systemd\|Running embedded tomcat on systemd]]
## Service Installation

- [Site Unreachable](https://help.talend.com/r/en-US/8.0/installation-guide-linux/installing-tomcat-service-on-systemd-systems)

---

# Standalone Tomcat

### References


1. [How To Install Apache Tomcat 10 on Ubuntu 20.04 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-10-on-ubuntu-20-04)

## Tomcat User

```bash
sudo useradd -m -d /opt/tomcat -U -s /bin/false tomcat
```

```bash
sudo chown -R tomcat:tomcat /opt/tomcat/
sudo chmod -R u+x /opt/tomcat/bin
```



### Installation

```bash
cd /tmp
```

### Download Tomcat

```bash
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.73/bin/apache-tomcat-9.0.73.tar.gz
```

```bash
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.89/bin/apache-tomcat-9.0.89.tar.gz
```

### Untar tomcat

```bash
mkdir -p /opt/tomcat
```

```bash
sudo tar xzvf apache-tomcat-9*tar.gz -C /opt/tomcat --strip-components=1
```

## Giving admin permission


### [[os/Linux/Ubuntu\|Ubuntu]]

```bash
sudo vim /opt/tomcat/conf/tomcat-users.xml
```

- Inside <tomcat-users/>

```xml
<role rolename="manager-gui" />
<user username="manager" password="manager" roles="manager-gui" />

<role rolename="admin-gui" />
<user username="admin" password="admin" roles="manager-gui,admin-gui" />

```

## Remove valve

- https://stackoverflow.com/a/39462403/7154462

```bash
sudo vim /opt/tomcat/webapps/manager/META-INF/context.xml
```

```bash
sudo vim /opt/tomcat/webapps/host-manager/META-INF/context.xml
```

***Comment* out valve**

```xml
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
            allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
```

## Systemd Service

```bash
sudo vim /etc/systemd/system/tomcat.service
```

```yaml
[Unit]
Description=Tomcat
After=network.target

[Service]
Type=forking

User=tomcat
Group=tomcat

Environment="JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-amd64"
Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"
Environment="CATALINA_BASE=/opt/tomcat"
Environment="CATALINA_HOME=/opt/tomcat"
Environment="CATALINA_PID=/opt/tomcat/temp/tomcat.pid"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

RestartSec=10
Restart=always

[Install]
WantedBy=multi-user.target

```

```
sudo systemctl start tomcat
sudo systemctl status tomcat
```

## Deploying web application

[Deploy a Spring Boot WAR into a Tomcat Server | Baeldung](https://www.baeldung.com/spring-boot-war-tomcat-deploy)


## [[SSL\|SSL]] Enable

- [Tomcat: CSR Creation & SSL Certificate Installation](https://www.digicert.com/kb/util/csr-creation-ssl-installation-tomcat.htm)
- [Apache Tomcat 7 (7.0.109) - SSL/TLS Configuration HOW-TO](https://tomcat.apache.org/tomcat-7.0-doc/ssl-howto.html)

## Listening on multiple ports


1. [Configuring Tomcat to Listen on Multiple Ports](https://www.eginnovations.com/documentation/eG-Installation-Guide/Configuring-Tomcat-to-Listen-on-Multiple-Ports.htm)


## Installing in [[Windows\|Windows]]

1. [Installing Tomcat](http://www.yorku.ca/jhuang/examples/tomcat-install.html)
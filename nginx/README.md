# nginx in front of jenkins

Build an nginx container in front of your jenkins server to enable SSL with Let's Encrypt.

# Install

- SSL certificates for your DNS
	- fullchain1.pem
	- privkey1.pem

Move certs to `certs` folder.

## Setup your host


```bash
# needs to be the same as the one already used
$ export PROJECT_NAME="dummy"
# the DNS that match with the SSL certificates
$ export PROJECT_DNS="dummy.com"
$ docker build -t nginx_jenkins .
$ docker run nginx_jenkins
```

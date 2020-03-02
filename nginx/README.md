# nginx in front of jenkins

Build an nginx container in front of your jenkins server to enable SSL with Let's Encrypt.

# Install

- SSL certificates for your DNS
	- fullchain1.pem
	- privkey1.pem

Move your certs to `certs` folder.

## Setup your host


```bash
# ensure fullchain1.pem and privkey1.pem files are present
$ ls certs/
# needs to be the same as the one already used
$ export PROJECT_NAME="dummy"
# the DNS that match with the SSL certificates
$ export PROJECT_DNS="dummy.com"
$ docker-compose up -d
```

No volume mounted from `certs`directory so you can safely delete it locally.

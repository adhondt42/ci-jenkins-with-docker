# ci-jenkins-with-docker

A Jenkins base image with docker-in-docker enabled and docker-compose, go and nodejs embedded.

**NOTE:**  You can edit the `docker-compose.yml` file to install docker-compose, go and nodejs version that fit to your needs.

# Setup your host

```bash
$ sudo mkdir -p /var/jenkins_home/{workspace,builds,jobs}
$ sudo chown -R 1000 /var/jenkins_home/ && sudo chmod -R a+rwx /var/jenkins_home/
```

# Setup your project

```bash
$ export PROJECT_NAME=dummy
$ git clone https://github.com/TommyStarK/ci-jenkins-with-docker.git
$ mv ci-jenkins-with-docker $PROJECT_NAME
$ cd $PROJECT_NAME
```

# Run the container

```bash
$ docker-compose up --build --detach
```

# Complete the installation

- Connect to the running container as root:

```bash
$ docker exec -ti -u root "${PROJECT_NAME}_jenkins" bash
```

- Now we are inside the container, run the following commands:

```bash
# change ownership of docker socket to jenkins user
$ chown jenkins /var/run/docker.sock

# exit
$ exit
```

- Test docker:

```bash
$ docker exec -ti "${PROJECT_NAME}_jenkins" bash

# This command should display all docker containers
$ docker ps -a
```

## Logs

```bash
$ docker logs -f `docker ps -aqf "name=${PROJECT_NAME}_jenkins"`
```

## Retrieve your ssh keys

```bash
$ docker exec -ti -u root "${PROJECT_NAME}_jenkins" bash
$ cat /root/.ssh/*
$ exit
```

---
title: simple Jenkins-in-Docker setup
date: 2020-03-08T13:13:44-05:00
tags: [operations]
---

I set up my home lab again with a new hard drive and decided to host Jenkins in Docker. [This page](https://jenkins.io/doc/book/installing/) details how to run Jenkins in a container, but the instructions lacked specifics of how to get things going on a single box. 

<!--more-->

So here's how I did it: I created two systemd configs (place these in `/etc/systemd/system` as `jenkins.service` and `jenkins-docker.service`):

```
[Unit]
Description=Jenkins
After=docker.service
Requires=docker.service

[Service]
Type=simple
User=jake
Group=jake
Restart=always
ExecStart=docker container run \
            --name jenkins \
            --rm \
            --user 0 \
            --network jenkins \
            --env DOCKER_HOST=tcp://docker:2376 \
            --env DOCKER_CERT_PATH=/certs/client \
            --env DOCKER_TLS_VERIFY=1 \
            --env JENKINS_OPTS='--prefix=/jenkins' \
            --publish 8080:8080 \
            --publish 50000:50000 \
            --volume /var/jenkins_home:/var/jenkins_home \
            --volume jenkins-docker-certs:/certs/client:ro \
            jenkinsci/blueocean
ExecStop=docker stop jenkins

[Install]
WantedBy=multi-user.target
```

To the docker command I added `--user 0` because the docker containers that the Jenkins jobs were trying to use my user (1000) which obviously wasn't working. I also mounted the volume to my local ```/var/jenkins_home```. I also removed `--detach` since systemd expects commands to block.

Here's the other config:

```
[Unit]
Description=Jenkins Docker
After=docker.service
Requires=docker.service

[Service]
Type=simple
User=jake
Group=jake
Restart=always
ExecStart=docker container run --name jenkins-docker --rm \
            --user 0 \
            --privileged --network jenkins --network-alias docker \
            --env DOCKER_TLS_CERTDIR=/certs \
            --volume jenkins-docker-certs:/certs/client \
            --volume /var/jenkins_home:/var/jenkins_home \
            --publish 2376:2376 docker:dind
ExecStop=docker stop jenkins-docker

[Install]
WantedBy=multi-user.target
```

Similar changes here. 

To get things going run these commands:

```
systemctl reload-daemon
systemctl jenkins start
systemctl jenkins-docker start
```

Note: I actually abandoned this because there's something nice about having the jobs just run on the OS normally. E.g. I can use the Jenkins user's ssh keys for deployment without having to configure all that in the Jenkinsfile. Also I can install Go or other tools globally through apt instead of having to use a container inside a container. 

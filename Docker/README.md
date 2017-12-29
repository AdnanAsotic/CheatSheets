# Docker

* Uses host OS
* Volumes can share data
* Docker Daemon
* Docker Images (Manifest)
* Docker Containers
* Without Containers Time to shipping is long
* Container can be shipped everywhere
* Containers can contain malicious code !!!

## Docker-Engine / Docker-Runtime / Docker-Daemon

* Shippingyard. Infrastructure, Runtime
* Platform can be changed (Windows, CentOS, Ubuntu, Debian ...)

## Docker-Images

* List of everything in container as instructions how to build it
* To launch a container an image is needed
* are comprimed of multiple layers (images ?)
  * Base Image (rootfs) - UBUNTU OS [Layer1]
  * NGINX [Layer2]
  * Updates [Layer3]
  * Each Layer as unique ID
* Images are readonly

```Docker
# interactive with bash
# image will be pulled from docker-hub
docker run -it fedora /bin/bash

# list images
docker images

# pull image
docker pull fedora
```

## Docker-Container

* Runtime Construct
* Effectively running Linux
* Not with all features. Just the minimum

```Docker
# attach to docker container (bash for example)
docker attach [pid]

[Ctrl] + [P] + [Q]

# List all running containers
docker ps

# List all containers
docker ps -a
```
## Docker Hub

* Contains Repositories, Trusted.
* Repositories contain images
* hub.docker.com to search for images

## CODE

### DOCKER FILE

*Instructions to build image
*Any files or dirs will be included in build !!!

```Dockerfile
FROM ubuntu:15.04
MAINTAINER adnan.asotic@outlook.de
# Every run adds a new layer to image !!!
RUN apt-get update
RUN apt-get install -y nginx
RUN apt-get install -y golang
VOLUME /data
# Only executes at runtime and run it build time instruction
CMD ["echo", "Hello World"]

# Pass into container environment variables
ENV var1=Nigel var2=Poultron
# Can't be overriden Parameter is added as rgument
#ENTRYPOINT ["echo"]
```

```Docker
# Build new image
docker build -t helloworld:0.1 .
docker inspect [container-name]
```

```Dockerfile
FROM ubuntu
MAINTAINER Adnan Asotic

RUN apt-get install -y software-properties-common python
RUN add-apt-repository ppa:chris-lea/node.js
RUN echo "deb http://us.archive.ubuntu.com/ubuntu/ precise universe" >> /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y nodejs
#RUN apt-get install -y nodejs=0.6.12~dfsg1-1ubuntu1
RUN mkdir /var/www

ADD app.js /var/www/app.js

CMD ["/usr/bin/node", "/var/www/app.js"] 
```

### LIST CONTAINERS
```Docker
docker -ps
```

### LIST CONTAINERS
```Docker
docker stop [name|id]
```

### CREATE NETWORK
```Docker
docker network create --driver bridge isolated_network
docker run -d --net=isolated_network --name mongodb mongo
```

### PUSH CONTAINERS
```Docker
docker build -f "dockerfile" -t "username/image-name"
docker push repository
docker rmi
```


### START CONTAINER
```Docker
docker run -d -p --name adnan 80:80 kitematic/hello-world-nginx
```

### REMOVE CONTAINER
```Docker
docker rm e60dd0155591
```

1. Base which allows composing of imaging

## Docker Compose
> docker-compose

- For Servers, Deployment
- VirtualBox on Windows

### Start all Services
```Docker
docker-compose up
```

### DOCKER COMPOSE FILE
```Docker
version: '3'
services:
  web:
    build: .
    ports:
     - "5000:5000"
  redis:
    image: "redis:alpine"
```

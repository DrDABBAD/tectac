---
title:  docker
# Mongodb with docker import and export a database
date: 2017-09-12 00:00:00 +0300
description:
img: ./software.jpg # Add image post (optional)
tags:  [docker, mongodb]
---
## Fun facts

Docker written in Go, is container  a logical partition where we can run applications isolated from the rest of the system. Earliest example of a Contianer is Unix Chroot allowed system admins to run programs in a kind-but-not-really-isolated filesystem.


## Installation

## Getting help

docker help
docker COMMAND --help
docker info

See []()

## Basic Commands

docker version
 docker info

Every day docker Commands:

To **Show images on local host**

docker images

The out put form this shows two columns TAG and REPOSITORY where tag corresponds to version of the image and REPOSITORY to the name


To **Show running images  i.e containers**

 docker ps --all

This output:
* CONTAINER_ID : A Unique ID for the container that was launched.
* IMAGE : This was the IMAGE that you launched i.e. busybox
* COMMAND

To run a container

docker run \<image-name\>

or
docker run -t -i busybox

Which means run interactively and attach to tty input so you can interact with a command line of the docker image.

## Building images

Starting from scratch use alpine or busybox
but images exist for most usual situations e.g mongodb mongo-express

To build images you use a dockerfile. This support Key several commands supported like FROM, CMD, ENTRYPOINT, VOLUME, ENV.

Running the docker file

## Data volumes

Containers are Ephemeral and once a container is removed, it is gone. To manage data and state within Docker containers, you use Volumes.

* Data volumes
* Data volume containers

## [Docker Compose](https://docs.docker.com/compose/)

A CLI tool for defining and running multi-container Docker applications.
Generally the tool is used with a docker-compose file  build  and  muliple containers specified in the YAML file.

For information on version see [compose specification](https://docs.docker.com/compose/compose-file/ )and  [Versioning](https://docs.docker.com/compose/compose-file/compose-versioning/)
Currently use  version 3.9 for Docker engine above 19.03.0 (check this)

### Yaml file key words



## Kubenetes

How is this different from docker, Kubentes handles distributed operations over multiple servers.


[See](https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG/CHANGELOG-1.20.md#deprecation)

[Read](https://semaphoreci.com/blog/kubernetes-vs-docker)

## Developing Dockerised .NET and .NET Core Applications


## Learning Resources

[Official Docker Documentation](https://docs.docker.com/)
[Docker Try It](https://www.docker.com/tryit/)
[Free Docker Training from Docker](https://training.docker.com/)
[Awesome Docker](https://github.com/veggiemonk/awesome-docker)
[Docker Cheat Sheet](https://github.com/wsargent/docker-cheat-sheet)
[Docker How To’s](https://github.com/botchagalupe/DockerDo)
[Container Tutorials](http://containertutorials.com/)

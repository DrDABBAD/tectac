
# Building a mongodb csv import App

Steps involved:

1. Setup your Nodejs application.
2. Create Dockerfile’s for each service.
3. Define services using the Compose file.
4. Run docker-compose to build the application.

## Docker and Dockerfile

Key concepts
**Docker image** is a template that is used to create a docker container.
**Docker container** is a instance of docker image containing all the components needed to run.

* docker files may be in project root or other directory. Typically  they are named 'dockerfile'.
* Comments may start with  # at a [line start only](https://docs.docker.com/engine/reference/builder/#format)

```dockerfile
# FROM Creates layers of dependencies like we could build an OS layer.
FROM alpine:latest
# RUN allows us to install linux packages.
RUN apk add — no-cache nodejs npm
WORKDIR /app
# COPY adds files from Docker client’s current directory.
COPY . /app
COPY package.json /app
# RUN allows us to install your application and packages required for it.
RUN npm install
COPY . /app
EXPOSE 8080
# CMD specifies a list of command to run within a Container.
CMD ["node", "app.js"]
```



## mongo in db

## Node in docker

1. Create App directory
2.  create docker file
Basic docker App using dockerfile


## Microservices connect

## Create an Express App


## Install App dependencies

## Create App models


## Create connection  nodejs app to mongodb


## Resources
[Node login App](https://github.com/Rammohan-bitzop/login-app)
[Docker mongodb Nodejs](https://medium.com/zenofai/how-to-build-a-node-js-and-mongodb-application-with-docker-containers-15e535baabf5)
[Comments in dockerfile](https://stackoverflow.com/questions/36710459/how-do-i-make-a-comment-in-a-dockerfile)
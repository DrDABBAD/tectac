---
title: Mongodb, docker and import export of database.
# Mongodb with docker import and export a database
date: 2017-09-12 00:00:00 +0300
description:
img: ./software.jpg # Add image post (optional)
tags:  [docker, mongodb]
---





## Prequisites, docker container for mongodb.

build  mongodb docker container with docker-compose.yml

```yaml
version: "3.8"
services:
mongodb:
image : mongo
container_name: mongodb
environment:
- PUID=1000
- PGID=1000
volumes:
- /home/<user>/mongodb/database:/data/db
ports:
- 27017:27017
restart: unless-stopped
```

Note:
Version of docker compose

WSL or commandline  or dos cml for starting docker ?

### volume commands
 List docker volumes
 docker volume ls
Ibspect volume
docker volume inspect acc_mongodata
Delect volume
docker volume rm my-vol

### mapping docker volume to dos directory

You can not use native Windows path formats for your host directory. Instead, you need to convert your path into a quasi-Linux format.
docker run -it --volume <host directory>:<target directory>
Example
docker run -it --volume //c/Users/david/my_project:/home/project ubuntu:latest

#### But what about docker compose

## Import and Export mongodb from docker container

### Using mongo tools

mongodump --uri 'mongodb://localhost:27017/yourdatabase' --archive=<your file> --gzip
mongorestore --uri 'mongodb://remotehost:27017/yourdatabase' --archive=<your file> --gzip

### But what if you don't have mongo on your local machine?

For the export then use:

docker exec -i <container_name> /usr/bin/mongodump --username <username> --password <password> --authenticationDatabase admin --db <database_name> --out /dump
docker cp <container_name>:/dump ~/Downloads/dump

For the import its a bit more complicated.

1. You need a user and access rights for the database to import.These are held in the admin database.
   There are other ways to do this (document latter).
```mongocli
use admin

db.createUser({
    user: "username",
	pwd: passwordPrompt(),
	roles:[{role: "readWrite" , db:"<database_name>"}]})
```

2. copy dump file to docker container  then restore the file

```docker
docker cp ~/Downloads/dump <container_name>:/<dumpdir>
docker exec -i <container_name> /usr/bin/mongorestore --username <username> --password <password> --authenticationDatabase admin --db <database_name> /<dumpdir>/<database_name>
```

*Does docker cp create the destination directory?*

This is not clear from the documentation, but looks as though `docker cp` does *not* create parent directories for `DEST_PATH`.

3. Clean up

```docker
 docker exec -it <container_name> /bin/bash

```

then:

```bash
rm -rf /dump
```

## resources

(https://stackoverflow.com/questions/61400292/import-a-mongo-database-into-a-docker-container)
(https://github.com/moby/moby/issues/20920)
[dump and pump data](https://davejansen.com/how-to-dump-restore-a-mongodb-database-from-a-docker-container/)
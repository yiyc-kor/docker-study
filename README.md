# docker-study

## Summary: How to use docker (Web Service)

### Make DB docker
Mysql
```
docker run --name [NAME] -e MYSQL_ROOT_PASSWORD=[ROOT_PASSWORD] -d\
	-p [HOST_PORT]:[GUEST_PORT] -v [HOST_PATH]:[GUEST_PATH] mysql:[VERSION]
```
cf)
```
docker run --name db -e MYSQL_ROOT_PASSWORD=db123 -d -p 33066:3306 -v C:\shared:/data mysql:5.6
```

### Make web server

```
docker search centos					# Also can search in Docker Hub
docker run -it --name [NAME] -d -v [HOST_PATH]:[GUEST_PATH] [DB_DOCK_NAME]:[NICKNAME] centos:[VERSION] --link /bin/bash	# access to DB using [NICKNAME] for url
ctrl + p,q
docker ps
docker exec -it server /bin/bash
ctrl + p,q
docker stop server
docker ps -a
docker start server
docker exec -it server /bin/bash

```
cf)
```
docker run -it --name web -d -v C:shared:/data --link db:db -p 8080:8080 -p 8000:8000 ubuntu:18.04 /bin/bash
```

## Start making image

```
docker run -p [HOST_PORT]:[CONTAINTER_PORT] --name [IMAGE_NAME] [REPO]
```

example:

```
docker run -p 73306:3306 --name db-server centos:7
```

## Readings

begin docker

https://subicura.com/2017/01/19/docker-guide-for-beginners-2.html

Docker image save&load&export&import

https://www.leafcats.com/240

Docker How to

http://pyrasis.com/Docker/Docker-HOWTO

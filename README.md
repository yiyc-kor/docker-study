# docker-study

## Simple summary

Check all container

```
docker ps -a
```

Start container
```
docker start [CONTAINER_NAME]
```

delete containter
```
docker rm [CONTAINER_NAME]
```

Make container
```
docker run -it --name [CONTAINER_NAME] -d -v [HOST_PATH]:[GUEST_PATH] --link [DB_DOCK_NAME]:[NICKNAME] centos:[VERSION] /bin/bash

```

Exec container
```
docker exec -it tbot-web /bin/bash
```

Commit container
```
docker commit -a [AUTHER] -m [MESSAGE] [CONTAINTER_NAME] [IMAGE_NAME]:[TAG]
```

Check images
```
docker images
```

Delete Docker image
```
docker rmi [IMAGE_NAME]
```

## How to make docker for web service

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
docker run -it --name [NAME] -d -v [HOST_PATH]:[GUEST_PATH] [DB_DOCK_NAME]:[NICKNAME] --link centos:[VERSION] /bin/bash	# access to DB using [NICKNAME] for url
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

### Use Jupyter Notebook

```
$ docker run -p 8888:8888 -v %cd%:/home/jovyan/work/ --name jupyter_notebook jupyter/datascience-notebook:python-3.7.6
```


### Notes

Pleas note the shared folder!!!

## Start making image

```
docker run -p [HOST_PORT]:[CONTAINTER_PORT] --name [IMAGE_NAME] [REPO]
```

example:

```
docker run -p 73306:3306 --name db-server centos:7
```

## Readings

* begin docker

https://subicura.com/2017/01/19/docker-guide-for-beginners-2.html

* Docker image save&load&export&import

https://www.leafcats.com/240

* Docker How to

http://pyrasis.com/Docker/Docker-HOWTO

* Nvdia Docker

https://ko-kr.facebook.com/notes/%EC%8B%A0%ED%98%84%EA%B0%91/1nvidia-docker-%EA%B8%B0%EB%B0%98-tensorflow-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/1187222141322502/

http://haanjack.github.io/docker/2017/12/01/nvidia-docker-ngc.html

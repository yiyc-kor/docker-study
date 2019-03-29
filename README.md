# docker-study

## Summary: How to use docker
```
docker run -it --name server centos /bin/bash
ctrl + p,q
docker ps
docker exec -it server /bin/bash
ctrl + p,q
docker stop server
docker ps -a
docker start server
docker exec -it server /bin/bash

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



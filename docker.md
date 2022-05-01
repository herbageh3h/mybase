# Quick Start

```
docker version
docker image ls
docker container ls
docker ps
docker log mysql
docker exec -it mysql bash
```

```
docker run -d -p 80:80 docker/getting-started
```

# Roadmap

1. image
2. container

# FAQ

### How to install on Mac?

```
brew install --cask docker
```

### How to install and run mysql container?

```
docker pull mysql/mysql-server:latest
docker run --name=mysql -d mysql/mysql-server:latest
```

### How to accelerate?

see [accelerator](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors).

### Where to find docker images?

see [docker hub](https://hub.docker.com/).

### How to delete all containers?

docker kill $(docker ps -aq); docker rm $(docker ps -aq)

### How to detach wihtout stopping the container?

^P ^Q => hotkey to detach

### How to install?

yum -y install docker-ce
brew cask install docker
For centos: https://docs.docker.com/install/linux/docker-ce/centos/#install-docker-ce-1

### How to start?

sudo systemctl start docker

### How to test?

docker run hello-world

### How to find out version?

docker version

### Hot to find out the location of the configuration file?

/etc/docker/daemon.json

### How to run?

```
docker run -d --name myblog -p 8000:80 --link mydb:mysql wordpress
docker run --name mydb -e MYSQL_ROOT_PASSWORD=root -d mysql
docker run -d -p 8080:8080 --name mytomcat tomcat
docker run -dit redis => -d means run in background
docker run -it --rm opensuse bash
docker run -it --rm --net="host" -v `pwd`:/src redis
docker run -it --rm --link myredis:redis redis redis-cli -h redis -p 6379
```

### How to list all images?

sudo docker image ls

### How to list all containers?

sudo docker container ls
docker container ls -a

### How to check container logs?

sudo docker container logs myredis

### How to stop container?

docker container stop
docker container start
docker container restart

### How to connect to container?

docker exec -it 8c87 bash

### How to export/import container snapshot?

docker export
docker import  => load container snapshot from local file
docker load => load image from local file

### How to delete a container?

docker container rm myredis
docker container prune

### How to search?

docker search centos

### How to share data between container and host?

through volume
docker run --name centos -it -v /home/herb/share:/root/share centos
docker run -v /home/herb:/mnt -it spacevim bash

### How to operate on volumes?

docker volume ls
docker volume create myvol
docker volume inspect myvol
docker volume rm myvol

### How to copy file?

docker cp mynginx:/etc/nginx/nginx.conf /home/herb/data/nginx.conf

### How to build?

docker build -t hello-world .

### How to add aliyun accelerator?

https://cr.console.aliyun.com/#/accelerator
if you can't restart docker after adding the registry mirror, make sure to uncheck 'Securely store docker logins in macos keychains.'

### How to avoid permission denied problem?

sudo groupadd docker
sudo usermod -aG docker huanghao
sudo chown root:docker /var/run/docker.sock

# Docker command examples

```
docker help run
docker build -t my-image .
docker run -d -it \
  --name=my-app \
  --rm \
  -h my-app-host -p 3000:3000 -v /data/app/myapp/share:/data -e ROLE="master" \
  --link my-mongo:mongo \
  -w /src \ => -w means setting working directory
  --volume-from jenkins-keys \
  --restart always
  my-image
docker stop my-container
docker rm -v my-container
docker restart my-container
docker kill my-container
docker start my-container
docker container ls -a
docker container prune
docker attach my-container
docker ps -aq
docker pull jenkins/jenkins:lts
docker save -o jenkins.tar jenkins/jenkins
docker load -i jenkins.tar
docker logs -f jenkins
docker version
docker info
docker images
docker rmi 18a77cfec765
docker export jenkins | gzip > jenkins.gz
zcat jenkins.gz | docker import - jenkins
docker commit jenkins hw3a/jenkins:1
docker inspect my-container
docker network ls
docker network prune
docker cp nginx:/etc/nginx/nginx.conf /data/app/nginx/
docker search prometheus
```

# Dockerfile examples

```
FROM php:7.0-apache
ARG http_port=8080
USER jenkins
COPY src/ /var/www/html
EXPOSE 80 443
WORKDIR /app  => set /app as current directory, used in the following RUN, COPY, ADD, etc.
VOLUME ["/var/www", "/var/log/apache2", "etc/apache2"]
RUN cd /app; npm install
CMD ["node", "app.js"] => default execution scripts
```

# Options

```
-h, --hostname
-i, --interactive
-t, --tty
-e, --env
--rm => Automatically remove the container when it exits.
```

# Links

<https://github.com/yeasy/docker_practice/blob/master/SUMMARY.md>
<https://alexanderzeitler.com/articles/docker-machine-and-docker-compose-developer-workflows/>

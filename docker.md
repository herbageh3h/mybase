# Quick Start

```
docker version
docker pull nginx
docker images
docker ps
docker container ls
docker stop <container_id|container_name>
docker start <container_id|container_name>
docker logs mysql
docker exec -it mysql bash
docker build -t hw3aweb:latest .
docker tag hw3a:latest hw3a:1
docker inspect <webserver:container_name>
```

```
docker run -d -p 80:80 nginx:latest => host port : container port
```


# Roadmap

1. image
2. container
3. volume
4. docker file


# Examples

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

# Links

+ [yeasy/docker_practice](https://github.com/yeasy/docker_practice/blob/master/SUMMARY.md)
+ [Workflows: using Docker Machine and Docker Compose together in development](https://alexanderzeitler.com/articles/docker-machine-and-docker-compose-developer-workflows/)
+ [amigos docker tutorial video](https://www.youtube.com/watch?v=p28piYY_wv8)


# FAQ

## What are those frequent used pull images?

```
docker pull nginx:alpine
docker pull node:alpine
```

## How to name a container?

```
docker run -d -p 80:80 --name webserver nginx:latest
```

## How to install on Mac?

```
brew install --cask docker
```

## How to install on DigitalOcean?

<https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04>

## How to install on centos?

```
yum -y install docker-ce
brew cask install docker
```
For centos: https://docs.docker.com/install/linux/docker-ce/centos/#install-docker-ce-1

## How to install and run mysql container?

```
docker pull mysql/mysql-server:latest
docker run --name=mysql -d mysql/mysql-server:latest
```

## How to accelerate?

see [accelerator](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors).

## Where to find docker images?

See [docker hub](https://hub.docker.com/).
```
docker login
docker push herbageh2h/webserver
```

## How to delete all containers?

```
docker kill $(docker ps -aq); 
docker rm $(docker ps -aq)
```

## How to detach wihtout stopping the container?

```
^P ^Q  "hotkey to detach
```

## How to start?

```
sudo systemctl start docker
```

## How to test?

```
docker run hello-world
```

## How to find out version?

```
docker version
```

## Hot to find out the location of the configuration file?

/etc/docker/daemon.json

## How to run?

```
docker run -d --name myblog -p 8000:80 --link mydb:mysql wordpress
docker run --name mydb -e MYSQL_ROOT_PASSWORD=root -d mysql
docker run -d -p 8080:8080 --name mytomcat tomcat
docker run -dit redis => -d means run in background
docker run -it --rm opensuse bash
docker run -it --rm --net="host" -v `pwd`:/src redis
docker run -it --rm --link myredis:redis redis redis-cli -h redis -p 6379
docker run -d -p 8080:80 -p 80:80 nginx:latest
```

## How to list all images?

```
docker images
docker image ls
```

## How to list all containers?

```
docker container ls
docker container ls -a
```

## How to check container logs?

```
docker container logs myredis
```

## How to stop container?

```
docker container stop
docker container start
docker container restart
```

## How to connect to container?

```
docker exec -it 8c87 bash
```

## How to export/import container snapshot?

```
docker export
docker import    "load container snapshot from local file
docker load    "load image from local file
```

## How to delete a container?

```
docker rm <container_id|container_name>
docker rm $(docker ps -aq)
docker container prune
docker rm -f <container_id|container_name> :: -f means force.
```

## How to search?

```
docker search centos
```

## How to share data between container and host?

use volume
```
docker run --name centos -it -v /home/herb/share:/root/share centos
docker run -v /home/herb:/mnt -it spacevim bash
docker run -d -p 80:80 --name webserver -v /home/jeff/nginx/profile:/usr/share/nginx/html nginx:latest
docker run --volumes-from <webserver:container_name> nginx => New container mount volume of webserver.
```

```
docker volume ls
docker volume create myvol
docker volume inspect myvol
docker volume rm myvol
```

## How to copy file?

```
docker cp mynginx:/etc/nginx/nginx.conf /home/herb/data/nginx.conf
```

## How to build?

```
docker build -t hw3aweb:latest .
```

## How to avoid permission denied problem?

```
sudo groupadd docker
sudo usermod -aG docker huanghao
sudo chown root:docker /var/run/docker.sock
```

## How to use docker ps command?

```
docker ps
docker ps -a
```

## How to use dockerfile?

Dockerfile is inside your project root directory.

Use `docker build` to build image using Dockerfile.
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

```
FROM nginx:latest
ADD . /usr/share/nginx/html
```

```
FROM node:latest
WORKDIR /app => In container, create or use /app as main work directory.
ADD package*.json ./ => package.json is hardly changed, so to use cache, we need to put it as early as possile.
RUN npm install => Use cache, don't need to install everytime. Only when package.json changed, it needs to install everything again.
ADD . . => Add current directory to /app in container.
CMD node index.js
```

## How to use .dockerignore?

Ignore some files during docker image building.
```
node_modules
Dockerfile
.git
```

## How to use docker logs?

```
docker logs -f <webserver:container_name> :: -f means follow.
```

## What are those docker run options?

```
-h, --hostname
-i, --interactive
-t, --tty
-e, --env
--rm => Automatically remove the container when it exits.
```

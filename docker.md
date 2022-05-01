# Docker

## Quick Start

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

## FAQ

#### 1. How to install on Mac?

```
brew install --cask docker
```

#### 2. How to install and run mysql container?

```
docker pull mysql/mysql-server:latest
docker run --name=mysql -d mysql/mysql-server:latest
```

#### 3. How to accelerate?

see [accelerator](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors).

#### 4. Where to find docker images?

see [docker hub](https://hub.docker.com/).

## Terms

* Container :: 容器
* Image :: 镜像

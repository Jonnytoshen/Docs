# Docker常用命令
### 1.将远程仓库的镜像pull到本机
```
$ docker pull IMAGE
```
### 2.查看本机镜像列表
```
$ docker images
$ docker image ls
```
### 3.查看本机容器列表
```
$ docker container ls
```
### 4.删除镜像
```
$ docker rmi IMAGE-ID
```
### 5.启动容器
```
$ docker start CONTAINER-ID
```
### 6.重启容器
```
$ docker restart CONTAINER-ID
```
### 7.停止容器
```
$ docker stop CONTAINER-ID
```
### 8.删除容器
```
$ docker rm -f CONTAINER-ID
```
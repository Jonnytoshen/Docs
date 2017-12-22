# Docker常用容器使用
此文档的所有操作都是在ubuntu 16.4环境下完成的，如果是第一次使用，您得先安装好Docker。同时我全部将数据文件和应用程序文件（代码）都放在主机上用-v命令映射到容器中，这样方便维护和备份。
## 1.Postgres
**参考内容：**  
https://store.docker.com/images/postgres  
https://docs.docker.com/samples/library/postgres/  
1. pull this image
```
$ docker pull postgres:9.6
```
> “9.6”为镜像的版本或标签（Tag）,一般来说也对应Postgres的版本。  
1. 运行容器
```
$ docker run -it --rm -v PGDATA:/var/lib/postgresql/data --name CONTAINER-NAME -p PORT:5432 -d postgres:9.6
```
> PGDATA：为主机数据文件目录，此目录下应包含文件postgresql.conf，此文件为postgres配置文件，如果要设置postgres其他主机可以连接，还需要文件pg_hba.config。
- How to get the data file  
在Ubuntu下postgres数据文件通常是在/var/lib/postgresql/9.6/main，我们需要先停掉postgres服务，然后将些目录下的所有文件拷贝或打包。

```
$ sudo su   
$ service postgresql stop
$ cd /var/lib/postgresql/9.6/main
$ tar -cvf /app/data.tar ./
$ mkdir /app/postgres
$ cd /app/postgres
$ tar -xvf /app/data.tar
```
> 这样我们数据文件（PGDATA）的路径为/app/postgres
- How to get the defautl config

```
docker run -i --rm postgres:9.6 cat /usr/share/postgresql/postgresql.conf.sample > /app/data/postgresql.conf
```
## 2.Nodejs
**参考内容：**  
https://store.docker.com/images/node  
1. Pull this image

```
$ docker pull node
```
2. Run this image

```
docker run -it --rm --name CONTAINER-NAME -v NODEJS-APP:/usr/src/app -w /usr/src/app -p PORT:PORT -d node:latest SCRIPT

```
> NODEJS-APP：nodejs应用程序在主机上的路径；
PORT：第一个PORT是主机上的端口，就是你正常访问要用的端口，第二个PORT为容器中项目使用的端口；
SCRIPT：用来启动项目的命令，比如：node .|node ./bin/www
## 3.Nginx
**参考内容：**  
https://store.docker.com/images/nginx  
1.Pull this image
```
$ docker pull nginx
```
2.Run this image
```
$ docker run --name CONTAINER-NAME -v NGINX-CONFIG:/etc/nginx/nginx.conf:ro -v WWWROOT:/usr/share/nginx/html -p PORT:80 -d nginx
```
> NGINX-CONFIG：nginx配置文件在主机上的路径，比如：~/config/nginx.config；
WWWROOT：应用程序的目录路径；
PORT：要使用的端口号；
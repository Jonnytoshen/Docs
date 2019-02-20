# Mysql 的使用

## 安装（Ubuntu）
```
$ sudo apt-get intsall mysql-server
```

## 启动、停止、重启和查看Mysql状态
1. 启动
```
$ sudo service mysql start
```
2. 停止
```
$ sudo service mysql stop
```
3. 重启
```
$ sudo service mysql restart
```
4. 查看Mysql状态
```
$ sudo service mysql status
```

## 用户
1. 使用root用户进入mysql命令行。
```
$ sudo mysql -u root -p
```
2. 查看所有用户
```
mysql> SELECT * FROM mysql.user;
```
3. 创建用户 - [详细文档](https://dev.mysql.com/doc/refman/5.6/en/create-user.html)
```
mysql> CREATE USER 'username' IDENTIFIED BY 'password';
```
4. 为用户添加可访问的数据库 - [详细文档](https://dev.mysql.com/doc/refman/5.6/en/grant.html)
```
mysql> GRANT ALL ON databaseName.* TO username;
```
5. 删除用户 - [详细文档](https://dev.mysql.com/doc/refman/5.6/en/drop-user.html)
```
mysql> DROP USER username;
```

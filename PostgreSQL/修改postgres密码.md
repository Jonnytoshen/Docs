# 修改PostgreSQL数据库默认用户postgres的密码
1. 登录postgresql
```
$ sudo -u postgres psql                
```
2. 修改postgres登录密码
```
$ ALTER USER postgres WITH PASSWORD '密码';
```
3. 退出postgresql客户端
```
$ \q
```
# 导出数据库为sql文件
1. 导出所有数据表结构和数据
```
$ pg_dump -h localhost -U postgres my-database > db_with_data.sql
```
- localhost：数据库主机地址；
- postgres：数据库用户名；
- my-database：数据库名称；
- db_with_data.sql：导出的文件名称； 
2. 知道出数据表结构
```
$ pg_dump -h localhost -U postgres my-database -s > db_no_data.sql
```
- localhost：数据库主机地址；
- postgres：数据库用户名；
- my-database：数据库名称；
- db_no_data.sql：导出的文件名称； 
# 导入数据
```
$ psql -h localhost -U postgres -d my-database -f ./db_with_data.sql
```
- localhost：数据库主机地址；
- postgres：数据库用户名；
- my-database：数据库名称；
- ./db_with_data.sql：要导入的数据文件；
# [MySQL](https://hub.docker.com/_/mysql)

## RUN

### Simple
```bash
docker run --rm -it -e MYSQL_ALLOW_EMPTY_PASSWORD=true mysql
```

### Advanced
```bash
docker run -d -it -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root_pw123! -e MYSQL_USER=myuser -e MYSQL_PASSWORD=myuser_pw123! -e MYSQL_DATABASE=hibuz_db \
  --name mysql mysql:8.0.31-debian --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci --secure-file-priv=""
```
> * --secure-file-priv="" : This variable is used to limit the effect of data import and export operations, such as those performed by the LOAD DATA and SELECT ... INTO OUTFILE statements and the LOAD_FILE() function. These operations are permitted only to users who have the FILE privilege. If empty, the variable has no effect. This is not a secure setting.


### Use
``` bash
# Simple
docker exec -it <CONTAINER ID or NAME> mysql

# Advanced
docker exec -it mysql mysql -h127.0.0.1 -P3306 -uroot -p -Dhibuz_db
# In order to connect remotely, you have to '%' wildcard grant permissions on all DB'
# GRANT ALL ON *.* TO 'myuser'@'%';
# FLUSH PRIVILEGES;
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 8.0.31 MySQL Community Server - GPL

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| hibuz_db           |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)

mysql> exit
Bye
```
> 

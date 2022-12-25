# [MariaDB](https://hub.docker.com/_/mariadb)

## RUN

### Simple
```bash
docker run --rm -it -e MYSQL_ALLOW_EMPTY_PASSWORD=true mariadb
```

### Advanced
```bash
docker run -d -it -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root_pw123! -e MYSQL_USER=myuser -e MYSQL_PASSWORD=myuser_pw123! -e MYSQL_DATABASE=myuser_db \
  --name mariadb mariadb:10.10.2-jammy --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci --secure-file-priv=""
```
> * --secure-file-priv="" : This variable is used to limit the effect of data import and export operations, such as those performed by the LOAD DATA and SELECT ... INTO OUTFILE statements and the LOAD_FILE() function. These operations are permitted only to users who have the FILE privilege. If empty, the variable has no effect. This is not a secure setting.


### Use
``` bash
# Simple
docker exec -it <CONTAINER ID or NAME> mysql

# Advanced
docker exec -it mariadb mysql -h127.0.0.1 -P3306 -uroot -p -Dmyuser_db
# In order to connect remotely, you have to '%' wildcard grant permissions on all DB'
# GRANT ALL ON *.* TO 'myuser'@'%';
# FLUSH PRIVILEGES;
Enter password: 
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 3
Server version: 10.10.2-MariaDB-1:10.10.2+maria~ubu2204 mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [myuser_db]> show databases;
+--------------------+
| Database           |
+--------------------+
| myuser_db          |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.000 sec)

MariaDB [myuser_db]> exit
Bye
```

Spring - application.properties
```INI
spring.datasource.driverClassName=org.mariadb.jdbc.Driver
spring.datasource.url=jdbc:mariadb://127.0.0.1/myuser_db?autoReconnect=true&useUnicode=true&characterEncoding=utf8
```

Gradle - build.gradle
```Groovy
dependencies {
  runtimeOnly 'org.mariadb.jdbc:mariadb-java-client'
}
```
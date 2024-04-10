# [PostgreSQL](https://hub.docker.com/_/postgres)

## RUN

### Simple
```bash
docker run --rm -it -e POSTGRES_PASSWORD=root_pw123! --name psql postgres
```

### Advanced
```bash
docker run -d -it -p 5432:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=root_pw123! --name psql postgres
```

### Use
``` bash
# Simple
docker exec -it psql psql -U postgres

# Advanced
docker exec -it psql psql -U root
psql (16.2 (Debian 16.2-1.pgdg120+2))
Type "help" for help.

root=# select now();
              now
-------------------------------
 2024-04-10 12:01:47.702966+00
(1 row)

root=# exit
```
> 

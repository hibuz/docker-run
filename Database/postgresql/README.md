# [PostgreSQL](https://hub.docker.com/_/postgres)

## RUN

### Simple
```bash
docker run --rm -it -e POSTGRES_PASSWORD=root_pw123! --name postgres postgres
```

### Advanced
```bash
docker run -d -it -p 5432:5432 -e POSTGRES_DB=pgdb -e POSTGRES_USER=root -e POSTGRES_PASSWORD=root_pw123! --name postgres pgvector/pgvector:pg18
```

### Use
``` bash
# Simple
docker exec -it postgres psql -U postgres

# Advanced
docker exec -it postgres psql -U root -d pgdb

psql (18.0 (Debian 18.0-1.pgdg12+3))
Type "help" for help.

pgdb=# select now();
              now              
-------------------------------
 2025-10-05 03:54:58.920448+00
(1 row)

pgdb=# CREATE EXTENSION IF NOT EXISTS vector;
CREATE EXTENSION
pgdb=# CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION
pgdb=# CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
CREATE EXTENSION
pgdb=# CREATE TABLE IF NOT EXISTS vector_store (
        id uuid DEFAULT uuid_generate_v4() PRIMARY KEY,
        content text,
        metadata json,
        embedding vector(768)                                           
);
CREATE TABLE
pgdb=# CREATE INDEX ON vector_store USING HNSW (embedding vector_cosine_ops);
CREATE INDEX
pgdb=# \d
           List of relations
 Schema |     Name     | Type  | Owner 
--------+--------------+-------+-------
 public | vector_store | table | root
(1 row)

pgdb=# \d vector_store
                     Table "public.vector_store"
  Column   |    Type     | Collation | Nullable |      Default       
-----------+-------------+-----------+----------+--------------------
 id        | uuid        |           | not null | uuid_generate_v4()
 content   | text        |           |          | 
 metadata  | json        |           |          | 
 embedding | vector(768) |           |          | 
Indexes:
    "vector_store_pkey" PRIMARY KEY, btree (id)
    "vector_store_embedding_idx" hnsw (embedding vector_cosine_ops)

pgdb=# exit
```
> 

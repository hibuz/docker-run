# [MongoDB](https://hub.docker.com/_/mongo)

## RUN

### Simple
```bash
docker run --rm -it --name mongo mongo
```

### Advanced
```bash
docker run -d -it -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=root_pw123! --name mongo mongo:8.2.6-rc0
```

### Use
``` bash
# Simple
docker exec -it mongo mongosh test-db

# Advanced
docker exec -it mongo mongosh -u root -p root_pw123! --authenticationDatabase admin test-db

Current Mongosh Log ID: 69a3cff0b416c3610b8563b0
Connecting to:          mongodb://<credentials>@127.0.0.1:27017/test-db?directConnection=true&serverSelectionTimeoutMS=2000&authSource=admin&appName=mongosh+2.7.0
Using MongoDB:          8.2.6-rc0
Using Mongosh:          2.7.0

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/

test-db> show dbs
test-db> show dbs
admin   100.00 KiB
config   12.00 KiB
local    72.00 KiB
test-db> exit
```

# [Elasticsearch](https://www.elastic.co/docs/deploy-manage/deploy/self-managed/install-elasticsearch-docker-basic)

## RUN


### Simple
```bash
docker run --rm -it docker.elastic.co/elasticsearch/elasticsearch
```

### Advanced
```bash
docker run --name es01 -p 9200:9200 -it -m 6GB -e "xpack.ml.use_auto_machine_memory_percent=true" docker.elastic.co/elasticsearch/elasticsearch:9.1.5
```

### Use
``` bash
# Copy the generated elastic password and enrollment token. These credentials are only shown when you start Elasticsearch for the first time. You can regenerate the credentials using the following commands.
docker exec -it es01 /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana

WARNING: Owner of file [/usr/share/elasticsearch/config/users] used to be [root], but now is [elasticsearch]
WARNING: Owner of file [/usr/share/elasticsearch/config/users_roles] used to be [root], but now is [elasticsearch]
eyJ2ZXIiOiI4LjE0LjAiLCJhZHIiOlsiMTcyLjE3LjAuNDo5MjAwIl0sImZnciI6Ijk1ZGYwZGM2ZDhkY2JmM2E3ZTg2YmI5NzdhMjY4Mjc4MWUxMmY0M2ViNmQ0NjQ5Yjc0NWUzYmQzNGVlNDNiZjgiLCJrZXkiOiJxdHFuRFpvQk9nb3FnNTVXQ1pHQTo0MWg0VjdNSjNYZXhVVDdQbjNzNXV3In0=

# We recommend storing the elastic password as an environment variable in your shell. Example:
export ELASTIC_PASSWORD="eyJ2ZXIiOiI4LjE0LjAiLCJhZHIiOlsiMTcyLjE3LjAuNDo5MjAwIl0sImZnciI6Ijk1ZGYwZGM2ZDhkY2JmM2E3ZTg2YmI5NzdhMjY4Mjc4MWUxMmY0M2ViNmQ0NjQ5Yjc0NWUzYmQzNGVlNDNiZjgiLCJrZXkiOiJxdHFuRFpvQk9nb3FnNTVXQ1pHQTo0MWg0VjdNSjNYZXhVVDdQbjNzNXV3In0="

# Copy the http_ca.crt SSL certificate from the container to your local machine.
docker cp es01:/usr/share/elasticsearch/config/certs/http_ca.crt .

# Make a REST API call to Elasticsearch to ensure the Elasticsearch container is running.
curl --cacert http_ca.crt -u elastic:$ELASTIC_PASSWORD https://localhost:9200
```


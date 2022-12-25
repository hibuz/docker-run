# [Jenkins](https://hub.docker.com/r/jenkins/jenkins)

## RUN

### Simple
```bash
docker run --rm -it -p 8080:8080 jenkins/jenkins
```

### Advanced
```bash
docker run -d -it -p 8080:8080 -p 50000:50000 
  --restart=on-failure \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v jenkins_home:/var/jenkins_home \
  --name jenkins jenkins/jenkins:2.383-alpine-jdk17
```

### Use
- visit: http://localhost:8080
``` bash
# Show administrator password
docker logs jenkins
```

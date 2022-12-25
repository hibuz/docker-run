# [ubuntu](https://hub.docker.com/_/ubuntu)

## RUN

### Simple
```bash
docker run --rm -it ubuntu bash
```

### Advanced
> [hibuz/bash](https://github.com/hibuz/ubuntu-docker/blob/main/Dockerfile) includes, ubuntu user an packages(sudo, iputils-ping, net-tools, curl, vim, git)
```bash
docker run -d -it --privileged -u ubuntu --name ubuntu hibuz/bash:22.04
```

### Use
``` bash
docker exec -it ubuntu bash
ubuntu@a20993d3aa14:~$ cat /etc/issue
Ubuntu 22.04.1 LTS \n \l
```

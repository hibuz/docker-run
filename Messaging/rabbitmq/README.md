# [RabbitMQ](https://hub.docker.com/_/rabbitmq)

## RUN

### Simple
```bash
docker run --rm -it rabbitmq
```

### Advanced
```bash
docker run -d -it -p 5672:5672 -p 8080:15672 -e RABBITMQ_DEFAULT_USER=myuser -e RABBITMQ_DEFAULT_PASS=myuser_pw123! \
  -e RABBITMQ_DEFAULT_VHOST=myvhost \
  --name rabbitmq rabbitmq:3.11.5-management-alpine
```

### Use
- visit: http://localhost:8080

Spring - application.properties
```INI
spring.rabbitmq.host=127.0.0.1
spring.rabbitmq.port=5672
spring.rabbitmq.virtual-host=myvhost
spring.rabbitmq.username=myuser
spring.rabbitmq.password=myuser_pw123!
```

Gradle - build.gradle
```Groovy
dependencies {
  implementation 'org.springframework.boot:spring-boot-starter-amqp'
  testImplementation 'org.springframework.amqp:spring-rabbit-test'
}
```
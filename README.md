# Spring Boot Docker with OpenJDK 8

[![](https://images.microbadger.com/badges/version/arunramakani/spring-boot-docker.svg)](https://microbadger.com/images/arunramakani/spring-boot-docker "Get your own version badge on microbadger.com") [![](https://img.shields.io/docker/pulls/arunramakani/spring-boot-docker.svg)](https://img.shields.io/docker/pulls/arunramakani/spring-boot-docker.svg) [![](https://img.shields.io/docker/stars/arunramakani/spring-boot-docker.svg)](https://img.shields.io/docker/stars/arunramakani/spring-boot-docker.svg)

Features:
- OpenJDK 8 
- Spring profiles
- Custom JAVA_OPTS
- Wrapper script that enables application to take PID 1 & receive SIGTERM signals
- Debug mode

## Available environment variables

Name                    | Default   | Description
------------------------|-----------|------------------------------------
SPRING_PROFILES_ACTIVE  | dev   | Active Spring profiles
JAVA_OPTS               |       | JAVA_OPTS
DEBUG                   | false | Enable or disable debug mode
DEBUG_PORT              | 8000  | Debug port


## How to use ?

1. Simply extend your image from `arunramakani/spring-boot-docker` and set your application name as an environment variable:
    ``` Docker
    FROM arunramakani/spring-boot-docker
    
    ENV ARTIFACT_NAME my-spring-boot-application.jar
    ```

2. Copy your Spring Boot executable jar into an `assets` folder and build you image:
```docker build -t spring-boot-image . ```

3. Start your application:
    - Using Docker CLI

### Inject environment variables:
```docker run -d -p 8080:8080 -e JAVA_OPTS='-Xms256m -Xmx512m' SPRING_PROFILES_ACTIVE='test' spring-boot-image```

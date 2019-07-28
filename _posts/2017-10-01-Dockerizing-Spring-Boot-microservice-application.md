---
layout: post
title: Dockerizing Spring Boot microservice application
subtitle: - 2 minute read
category: technology
---

Assuming you have a [Spring Boot](https://projects.spring.io/spring-boot/) app built, tested and ready to be packaged in to a container for deployment.

There are multiple ways;

### Using DockerFile and building docker image

Create a file called Dockerfile in the application directory and add below commands;

```
FROM java:8
VOLUME /tmp
EXPOSE 8080
ADD /build/libs/myapp-1.0.jar app/myapp-1.0.jar
ENTRYPOINT ["java","-jar","app/myapp-1.0.jar"]
```

Now build the docker image
```
$ docker build -f Dockerfile -t myapp .
```
Now you should see your Docker image in the list
```
docker images
```

### Using Gradle plugin

I am using SpringBoot with [Gradle](https://gradle.org/), precisely *spring-boot-gradle-plugin:1.5.7.RELEASE*.

Well you can create separate app and then build Docker image manually, however when using Gradle there are good plug-ins available and one I am using is Transmode/gradle-docker plug-in [https://github.com/Transmode/gradle-docker](https://github.com/Transmode/gradle-docker)

**Gradle config for Docker using Transmode plug-in**

### Using Docker compose

Docker compose makes it easier to specify Docker dependencies and using Gradle dependency it makes it easier if you are using Spring boot apps for example.

These additional plugin configurations helps with this;
```
apply plugin: 'docker'
...

task buildDocker (type:Docker, dependsOn: build) {
	applicationName = jar.baseName
	dockerfile = file('Dockerfile')
	doFirst {
		copy {
			from jar
			into stageDir
		}
	}
}
```
Then if you run below it will create the Docker image like gradle-springboot

```
gradle build buildDocker
```
Then we add a Docker compose file docker-compose.yml in the project directory where we can specify any docker dependencies/linking;

```
'# docker-compose.yml
version: '3'

services: 
  docker-backendservice:
    image: backendservice:latest

  spring-boot-jpa-docker-webapp:
    image: gradle-springboot
    depends_on:
      - docker-backendservice
    ports:
      - 8080:8080

```
Then by running below we can see that two containers are created and linked;
```
docker-compose up
```

----
Once docker image is ready, you can run as below;
```
$ docker run -t --name myapp -p 8080:8080 myapp
```



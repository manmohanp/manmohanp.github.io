---
layout: post
title: Dockerizing Spring Boot microservice application
category: technology
---

Assuming you have a [Spring Boot](https://projects.spring.io/spring-boot/) app built, tested and ready to be packaged in to a container for deployment.

I am using SpringBoot with [Gradle](https://gradle.org/), precisely *spring-boot-gradle-plugin:1.5.7.RELEASE*.

Well you can create separate app and then build Docker image manually, however when using Gradle there are good plug-ins available and one I am using is Transmode/gradle-docker plug-in [https://github.com/Transmode/gradle-docker](https://github.com/Transmode/gradle-docker)

**Gradle config for Docker using Transmode plug-in**
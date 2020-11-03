---
title: 常用docker-compose.yml配置
date: 2020-11-03 11:01:12
tags: docker
categories: 后端环境
---

记录一些常用的`docker-composer.yml`配置文件
<!--more-->
1. mongo
```yaml
version: '3'
  services:
    mongodb:
      image: mongo
      container_name: mongo_test
      environment:
        - MONGO_INITDB_ROOT_USERNAME=admin
        - MONGO_INITDB_ROOT_PASSWORD=admin
      volumes:
        - /home/sun/mongotest/db:/data/db
        - /home/sun/mongotest/log:/var/log/mongodb
      ports:
        - 27017:27017
      restart: always
```
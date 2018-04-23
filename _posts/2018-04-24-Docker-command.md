---
layout: post
title:  "Docker基础命令"
categories: docker
tags:  docker基础
author: PPJoin
---

* content
{:toc}

## 搜索所有centos镜像
```bash
docker search centos
```
## 下载centos镜像
```bash
docker pull hidetarou2013/centos6-apache
```
## 查看所有镜像
```bash
docker images
```




## 删除某镜像
```bash
docker rmi hidetarou2013/centos6-apache
```
## 创建数据卷volume
名称为`portainer_data`,里面的文件一般在`/var/lib/docker/volumes/`目录下,可以供容器挂载
```bash
docker volume create portainer_data;
```
## 从镜像创建容器
容器名`centos` 端口`80`,`1013`,`55555`,`1194`,`8888`,基础镜像`hidetarou2013/centos6-apache`
```bash
docker run --name=centos -d -p 80:80 -p 1013:1013 -p 55555:55555 -p 1194:1194 -p 8888:8888 hidetarou2013/centos6-apache
```
## 列出所有容器
```bash
docker ps -a
```
## 进入某容器的命令行
```bash
docker exec -it centos /bin/sh
```
## 停止容器
```bash
docker stop centos
```
## 删除容器
```bash
docker rm -f centos
```

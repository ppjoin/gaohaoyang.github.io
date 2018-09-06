---
layout: post
title:  "Docker实践一些基础应用"
categories: Docker
tags:  Docker基础
author: PPJoin
---

* content
{:toc}

## 安装 portainer

WEB 管理 Docker 的工具，好用。
参数说明：名称 `Portainer_docker_web_cp`，设置开机自动启动 , 挂载数据卷 `portainer_data` , 开放端口 `9001`

```bash
docker run -d --name server_Portainer_docker_web_cp --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data -p 9001:9000 portainer/portainer;
```




## 安装 Mysql 服务端

名称 `server_mysql5`，设置开机自动启动，挂载宿主机 `/docker/mysql/data` 目录，对应容器里的 `/var/lib/mysql` 目录，开放端口`3306`，宿主机映射的端口为`3305`，容器参数 `MYSQL_ROOT_PASSWORD` 为 `12345678`

```bash
docker run -d --name server_mysql5 --restart=always -v /docker/mysql/conf.d:/etc/mysql/conf.d -v /docker/mysql/data:/var/lib/mysql -d -p 3305:3306 -e MYSQL_ROOT_PASSWORD=12345678 mysql:5.5;
```

## 安装 nginx + php5

此容器基于alpine极简系统。宿主机可以先建立个文件夹，存储 nginx 的网页文件，我这里是 `/docker/nginx/wwwroot`

```bash
docker run -d --name server_nginx_php56 --restart=always -p 80:80 -p 443:443 -v nginx_etc:/etc/nginx -v /docker/nginx/wwwroot:/var/www/html germanramos/nginx-php-fpm:v5.6.21;
```

## Alpine GUI 基础镜像

自带 novnc 网页视窗，novnc 的端口是 `5800`，浏览器打开即可访问。

作者还有 debian8 的镜像，相当不错：jlesage/baseimage-gui:debian-8-v3.2.2

```bash
docker run --name vnc -p 5800:5800 -p 5900:5900 jlesage/baseimage-gui:alpine-3.5-glibc;
```

## fluxbox + firefox + novnc 镜像

端口 `8083` 可以打开网页版 novnc ，里面运行着 firefox 浏览器。

```bash
docker run -d --name novnc_firefox -p 5900:5900 -p 8083:8083 -v novnc_firefox_01:/cfg samswett/x11-novnc-firefox;
```

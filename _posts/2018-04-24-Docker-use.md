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
Docker 管理工具 -- WEB浏览器下管理Docker
名称 `Portainer_docker_web_cp`，设置开机自动启动 , 挂载数据卷 `portainer_data` , 开放端口 `9001`
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

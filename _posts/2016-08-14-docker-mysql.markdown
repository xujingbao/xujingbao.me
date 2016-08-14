---
layout: post
title: 在Docker中使用MySQL
date: 2016-08-14 00:38:24.000000000 +09:00
tag: docker mysql 
---
![Gralde Logo](/assets/images/20160814/mysql-logo.png)  

#### 启动mysql
> docker run \  
> --name sxf-fd-mysql \   #容器名称  
> -v /docker/mysqldata:/var/lib/mysql  \  #挂载卷  
> -e MYSQL_ROOT_PASSWORD=my-secret-pw \ #root密码  
> -d \ #后台运行  
> -p 3306:3306 \ #端口映射  
> xujingbao/fd-mysql-5.6  #镜像  

#### 进入mysql
> docker exec -it container-id bash

#### 创建用户
> CREATE USER 'username'@'%' IDENTIFIED BY 'password';

#### 授权
> grant all privileges on *.* to 'username'@'%' identified by 'password';  
> grant all privileges on *.* to 'username'@'localhost' identified by 'password';

#### 设置密码
> SET PASSWORD FOR 'username'@'%' = PASSWORD("password");  
> SET PASSWORD FOR 'username'@'localhost' = PASSWORD("password");  
> SET PASSWORD = PASSWORD("newpassword");
---
layout:     post
title:      CentOS7安装MySQL5.7步骤
date:       2019-09-24
author:     BY
header-img: img/post-bg-kuaidi.jpg
catalog: true
tags:
    - Xcode
    - iOS
---

## 1,下载MySQL源安装包

	wget http://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm

## 2,安装MySQL源

	yum -y install mysql57-community-release-el7-11.noarch.rpm

### 3，安装MySQL服务器

```
yum install mysql-community-server
```

### 4，启动关闭MySQL服务器

```
systemctl start mysqld.service
```

### 5,查看MySQL运行状态

```
systemctl status mysqld.service
```

### 6，MySQL5.7安全性提高了会自动生成密码，使用：grep "password" /var/log/mysqld.log 查看初始密码

### 7，登录MySQL

```
mysql -u root -p
```

### 8,修改密码

```
SET PASSWORD = PASSWORD('YYBrhr_2018');
ALTER USER 'root'@'localhost' PASSWORD EXPIRE NEVER;
flush privileges;
注意：安全性提高，密码使用：大写小写特殊符号h格式详细查看该网址：https://blog.csdn.net/hello_world_qwp/article/details/79551789
```

### 9，远程连接授权

```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'YYBrhr_2018' WITH GRANT OPTION;//by后面是自己设置的密码
```

### 10，防火墙开放数据库端口（默认3306，可以在/etc/my.cnf中修改）

### 11，开放端口

```
firewall-cmd --permanent --add-port=3306/tcp
```

### 12：设置开机启动

```
systemctl enable mysqld
systemctl daemon-reload
```


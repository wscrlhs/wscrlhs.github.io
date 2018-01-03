---
layout: post
title: LNMP环境搭建
categories: 安装配置
tags:  lnmp
---

* content
{:toc}


## 安装mysql
- centos6  
` yum install mysql-server`
- centos7  
MySQL的社区仓库：https://dev.mysql.com/downloads/repo/yum/

- 安装步骤：
```bash
wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
rpm -ivh mysql-community-release-el7-5.noarch.rpm
yum update
yum install mysql-server
```




## 安装nginx  
- 安装步骤
```bash
yum install epel-release
yum -y install nginx
```

- Nginx 默认的HTML根目录是：/usr/share/nginx/html  
赋予权限  
`chown -R nginx:nginx html/`
### 配置nginx
- 打开文件/etc/nginx/conf.d/default.conf 
- 定义server容器

```bash
[...]
    server {
        listen 80;
        listen [::]:80 default_server;
        server_name _;
        root /usr/share/nginx/html;

        # 设置默认主页
        index index.php index.html index.htm;

        location / {
            # First attempt to serve request as file, then
            # as directory, then fall back to displaying a 404.
            try_files $uri $uri/ =404;
        }

        # PHP脚本转发至PHP-FPM解析
        location ~ \.php$ {
            try_files $uri =404;
            fastcgi_pass unix:/var/run/php-fpm/php-fpm.sock;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            fastcgi_index index.php;
            include fastcgi_params;
        }
    }
[...]
```
- 检查配置文件语法
`nginx -t`

## 安装php-fpm
- 此版本过低  
`yum install php php-mysql php-fpm`
- 更换yum源
```bash
　　#检查当前PHP的安装包
　　yum list installed | grep php
　　
　　#移除当前PHP的安装包，否则容易起冲突
　　yum remove php*
　　
　　#由于默认的YUM源无法升级PHP，所以需要添加第三方的YUM源，此处用到webtatic。
　　#因为是CentOS 6.5，所以用以下URL
　　rpm -Uvh http://mirror.webtatic.com/yum/el6/latest.rpm
　　#如果是CentOS 7.x
　　rpm -Uvh https://mirror.webtatic.com/yum/el7/epel-release.rpm
　　rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
　　
　　#查看YUM源上能用PHP安装包
　　yum list php*
　　
　　#安装PHP5.5及需要的扩展
　　yum install php55w php55w-devel php55w-common php55w-mysql php55w-pdo php55w-opacache php55w-xml
　　
　　#再次查看PHP版本，以确认安装是否成功
```
### 配置php-fpm
- 打开文件 /etc/php-fpm.d/www.conf
- 修改内容,如下
```bash
[...]
listen = /var/run/php-fpm/php-fpm.sock
[...]
listen.owner = nobody
listen.group = nobody
[...]
user = nginx
group = nginx
[...]
```

## 启动
```bash
service nginx start
service php-fpm start
service mysqld start
```

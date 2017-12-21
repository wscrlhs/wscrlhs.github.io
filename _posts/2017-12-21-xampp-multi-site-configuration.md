---
layout: post
title: Xampp 多站点配置
categories:  Xampp
tags: Xampp
---

* content
{:toc}

## hosts 文件中设置域名解析

- 找到`C:\Windows\System32\drivers\etc\hosts` 文件，打开编辑
- 在文件末尾添加两行域名解析记录，每行一个域名。前面为ip地址，空间用空格或者制表符隔开，后面是域名:

```
127.0.0.1 www.localhost.com
127.0.0.1 www.myproject.com
```

## Apache 中添加多域名支持

- 找到`xampp/apache/conf/extra/httpd-vhosts.conf `文件，打开编辑
- 去掉注释符号 `# NameVirtualHost *:80 ;`
- 文件末尾添加代码：

```
<VirtualHost *:80>
    DocumentRoot "/xampp/htdocs"
    ServerName www.localhost.com
    ErrorLog "logs/www.localhost.com-error.log"
    CustomLog "logs/www.localhost.com-access.log" combined
</VirtualHost>

<VirtualHost *:80>
    DocumentRoot "/xampp/htdocs/myproject"
    ServerName www.myproject.com
    ErrorLog "logs/www.myproject.comw-error.log"
    CustomLog "logs/www.myproject.com-access.log" combined
</VirtualHost>
```

## 重启Xampp服务
- 打开浏览器，输入www.localhost.com和www.myproject.com即可访问

---
layout: post
title: Linux下多线程下载工具 - Axel
categories: 安装配置 linux
tags:  linux
---

* content
{:toc}

Axel是一个命令行下载工具，支持多来源、多线程.

Axel tries to accelerate HTTP/FTP downloading process by using multiple connections for one file. 
It can use multiple mirrors for a download. Axel has no dependencies and is lightweight, so it might be useful as a wget clone on byte-critical systems.





## 安装

### Debian/Ubuntu安装
>
apt-get install axel

### CentOS安装
目前yum源上没有Axel，可以到http://pkgs.repoforge.org/axel/下载rpm包安装。

- 32位CentOS执行下面命令：

```bash
wget -c http://pkgs.repoforge.org/axel/axel-2.4-1.el5.rf.i386.rpm
rpm -ivh axel-2.4-1.el5.rf.i386.rpm
```

- 64位CentOS执行下面命令：

```bash
wget -c http://pkgs.repoforge.org/axel/axel-2.4-1.el5.rf.x86_64.rpm
rpm -ivh axel-2.4-1.el5.rf.x86_64.rpm
```

## 使用
假设已知多个来源，分别为url1，url2 等

> 
axel [options] url1 [url2] [url...]

### options(可选参数)
>
--max-speed=x , -s x         最高速度x  
--num-connections=x , -n x   连接数x  
--output=f , -o f            下载为本地文件f  
--search[=x] , -S [x]        搜索镜像  
--header=x , -H x            添加头文件字符串x（指定 HTTP header）  
--user-agent=x , -U x        设置用户代理（指定 HTTP user agent）  
--no-proxy ， -N             不使用代理服务器  
--quiet ， -q                静默模式  
--verbose ，-v               更多状态信息  
--alternate ， -a            Alternate progress indicator  
--help ，-h                  帮助  
--version ，-V               版本信息  


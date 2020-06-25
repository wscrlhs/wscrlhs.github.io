---
layout: post
title: 在Centos6.8环境下搭建svn服务
categories: 安装配置 svn
tags: svn
---

* content
{:toc}


## 安装svn
```
yum -y install subversion
```
## 创建svn仓库目录
```
mkdir -p /data/svn/repositories/mysvn
```

## 创建svn版本库
```
svnadmin create /data/svn/repositories/mysvn/
```




## svn配置

- 创建用户
```
vim /data/svn/repositories/mysvn/conf/passwd
#在里面增加用户，格式为：用户名 = 密码
```
- 设置权限
```
vim /data/svn/repositories/mysvn/conf/authz
#在里面增加权限   格式为：用户名 = rw (r:表示读，w:表示写),如
[mysvn:/]
yubb = rw
#mysvn为开始创建的版本库
```
- 修改svnserve.conf文件
```
vim /data/svn/repositories/mysvn/conf/svnserve.conf
#以下代码取消注释
anon-access = read //匿名用户可读
auth-access = write //授权用户可写
password-db = passwd //使用哪个文件作为账号文件
authz-db = authz //使用哪个文件作为权限文件
ealm =  /data/svn/repositories //认证空间名，版本库所在目录
```

## 启动svn服务
```
svnserve -d -r /data/svn/repositories/      //启动svn，注意目录，不包括mysvn
ps aux | grep svnserve      //查看启动情况
```
## 克隆
- 本地克隆
```
svn checkout svn://ip:/mysvn
```
- 远程克隆
```
svn checkout svn://localhost:/mysvn
```

## 遇到的问题
1. 在阿里云安装svn，客户端无法访问

   svn默认使用端口3690

    登录阿里云控制服务台，访问云服务器ECS-->本服务器-->实例-->管理-->本实例安全组->配置规则，添加安全组策略。

    ​

    ![](http://ww1.sinaimg.cn/large/73f02bfcgy1fmgmd1us34j20yk0380t2.jpg)

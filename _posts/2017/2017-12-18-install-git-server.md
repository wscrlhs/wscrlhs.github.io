---
layout: post
title: 在Linux上搭建Git服务
categories: 安装配置 git
tags: git
---

* content
{:toc}

### 创建一个 git 的用户和用户组，用来运行 git 服务
```
groupadd git
useradd git -g git
```
### 为 git 设置密码
```
passwd git
```

### 安装 git
```
yum install git # centos
apt-get install git # ubuntu
```




### 配置服务器
```
su git
mkdir .ssh && chmod 700 .ssh
touch .ssh/authorized_keys && chmod 600 .ssh/authorized_keys
chown -R git:git .ssh
```
### SSH 验证设置
```
cat ~/.ssh/id_rsa.pub  #在客户端执行
将客户端公钥拷贝到.ssh/authorized_keys
```

### 创建一个目录
```
cd /srv #切换到 srv 目录
mkdir gitrepo #新建目录
chown -R git:git /srv/gitrepo
```

### 初始化一个 git 仓库
```
cd /srv/gitrepo
git init --bare  project.git
```
### 克隆
- 本地克隆
```
git clone /srv/gitrepo/project.git
```
- 远程克隆
```
git clone git@ip:/srv/gitrepo/project.git
```
- 第一次提交
```
git push -u origin master
```

### 禁止开发者用户以系统用户 git 的身份登录服务器
```
cat /etc/shells   # see if `git-shell` is already in there.  If not...
which git-shell   # make sure git-shell is installed on your system.
sudo vim /etc/shells  # and add the path to git-shell from last command
```

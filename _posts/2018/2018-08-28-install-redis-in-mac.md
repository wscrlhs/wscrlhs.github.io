---
layout: post
title: 在Mac下安装Redis
categories: [redis,mac]
tags:
  - redis
  - mac
---

  * content
  {:toc}


## brew 安装redis
`brew install redis`

### 使用
```
# 开启服务
 brew services start redis
# 停止服务
 brew services stop redis
# 重启服务
 brew services restart redis
```

### 终端使用
- 开启服务
`redis-server`
- 开启客户端
`redis-cli`


## 安装phpredis扩展
brew 不再支持php-redis安装，所以使用编译安装的方法。
1. 下载phpredis源码
`https://nodeload.github.com/nicolasff/phpredis/zip/master`
2. 解压到`/usr/local/src`目录下后编译
```
phpize  ./configure --with-php-config=/usr/local/opt/php\@7.1/bin/php-config`
sudo make && make install
sudo make test
```
3. 移动编译好的redis.so文件
`cp /usr/local/src/phpredis-master/modules/redis.so   /usr/local/Cellar/php@7.1/7.1.21/pecl/20160303/`

4. 在php.ini文件后添加(/usr/local/etc/php/7.1)
```
[redis]
extension=redis.so
```

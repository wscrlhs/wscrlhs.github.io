---
layout: post
title:  在windows下安装Redis
categories: redis
tags:  redis
---

* content
{:toc}


## 下载
官网下载地址：[http://redis.io/download](http://redis.io/download
)

github下载地址：[https://github.com/MSOpenTech/redis/tags](https://github.com/MSOpenTech/redis/tags)

## 安装Redis
- 这里下载的是Redis-x64-3.2.100.zip ,解压到redismulu  
![](/assets/images/20190129001.png)

- 启动redis,执行命令`redis-server redis.windows.conf`,出现下图就启动成功了  
![](/assets/images/20190129002.png)

## 设置Reids服务
执行命令`redis-server --service-install redis.windows-service.conf --loglevel verbose`,将Redis添加到服务列表中  
![](/assets/images/20190129003.png)

## 常用的Redis服务命令

- Uninstalling the Service  
`redis-server --service-uninstall`

- Starting the Service  
`redis-server --service-start`

- Stopping the Service  
`redis-server --service-stop`

- Naming the Service  
```
redis-server --service-install --service-name redisService1 --port 10001
redis-server --service-start --service-name redisService1
redis-server --service-install --service-name redisService2 --port 10002
redis-server --service-start --service-name redisService2
redis-server --service-install --service-name redisService3 --port 10003
redis-server --service-start --service-name redisService3
```

## 为PHP5.6安装Redis扩展
### 下载php_redis.dll 和 php_igbinary.dll
[http://windows.php.net/downloads/pecl/releases/redis/](http://windows.php.net/downloads/pecl/releases/redis/)
[http://windows.php.net/downloads/pecl/releases/igbinary/](http://windows.php.net/downloads/pecl/releases/igbinary/)

**扩展类型选择**  
![](/assets/images/20190129004.png)

我的电脑配置是php5.6,x86,ts(Thread Safety）,VC11,所以下载的是php_redis-2.2.7-5.6-ts-vc11-x64.zip  
![](/assets/images/20190129008.png)
![](/assets/images/20190129005.png)

### 解压缩后把php_igbinary.dll和php_redis.dll拷贝到php的ext目录下  
![](/assets/images/20190129006.png)

### 修改php.ini文件，在文件末尾jiaru
```
; php_redis

extension=php_igbinary.dll

extension=php_redis.dll
```

### 重启apache服务，查看扩展有没有成功  
![](/assets/images/20190129005.png)

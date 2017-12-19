---
layout: post
title: Memcached的安装和使用
categories: memcached
tags: memcached
---

* content
{:toc}

# Memcached简介
Memcached是一个自由开源的，高性能，分布式内存对象缓存系统。

Memcached是一种基于内存的key-value存储，用来存储小块的任意数据（字符串、对象）。这些数据可以是数据库调用、API调用或者是页面渲染的结果。

Memcached简洁而强大。它的简洁设计便于快速开发，减轻开发难度，解决了大数据量缓存的很多问题。它的API兼容大部分流行的开发语言。

本质上，它是一个简洁的key-value存储系统。

一般的使用目的是，通过缓存数据库查询结果，减少数据库访问次数，以提高动态Web应用的速度、提高可扩展性。





# 安装
## Linux下安装memcached
* 首先要先安装libevent库
​       `yum install libevent libevent-deve`        自动下载安装（Redhat/Fedora/Centos）

* 自动安装
  `yum install memcached`
* memcached启动
  `service memcached start`
* memcached 停止
  `service memcached stop`

## Memcached连接
> **telnet HOST PORT**

​      `telnet 127.0.0.1 11211`

# Memcached 使用
## 存储命令
### set命令

**语法：**
> set 命令的基本语法格式如下：

```
set key flags exptime bytes [noreply]
value
```
**参数说明如下：**
- **key**：键值 key-value 结构中的 key，用于查找缓存值。
- **flags**：可以包括键值对的整型参数，客户机使用它存储关于键值对的额外信息 。
- **exptime**：在缓存中保存键值对的时间长度（以秒为单位，0 表示永远）
- **bytes**：在缓存中存储的字节数
- **noreply（可选）**： 该参数告知服务器不需要返回数据
- **value**：存储的值（始终位于第二行）（可直接理解为key-value结构中的value）

**实例**

以下实例中我们设置：

key → runoob

flag → 0

exptime → 900 (以秒为单位)

bytes → 9 (数据存储的字节数)

value → memcached

```
set runoob 0 900 9
memcached
STORED

get runoob
VALUE runoob 0 9
memcached

END
```
**输出**
如果数据设置成功，则输出：
```
STORED                                          `
```
输出信息说明：
- STORED：保存成功后输出。
- ERROR：在保持失败后输出。

### add命令

**语法：**

add 命令的基本语法格式如下：

```
add key flags exptime bytes [noreply]
value
```

参数说明如下：

- **key：**键值 key-value 结构中的 key，用于查找缓存值。
- **flags**：可以包括键值对的整型参数，客户机使用它存储关于键值对的额外信息 。
- **exptime**：在缓存中保存键值对的时间长度（以秒为单位，0 表示永远）
- **bytes**：在缓存中存储的字节数
- **noreply（可选）**： 该参数告知服务器不需要返回数据
- **value**：存储的值（始终位于第二行）（可直接理解为key-value结构中的value）

**实例**

以下实例中我们设置：

- key → new_key
- flag → 0
- exptime → 900 (以秒为单位)
- bytes → 10 (数据存储的字节数)
- value → data_value

```
add new_key 0 900 10
data_value
STORED
get new_key
VALUE new_key 0 10
data_value
END
```

**输出**

如果数据添加成功，则输出：

```
STORED
```

输出信息说明：

- **STORED**：保存成功后输出。
- **NOT_STORED**：在保持失败后输出。

## 查找命令
### get命令

Memcached get 命令获取存储在 key(键) 中的 value(数据值) ，如果 key 不存在，则返回空。
```
get key
```
### gets命令

Memcached gets 命令获取带有 CAS 令牌存 的 value(数据值) ，如果 key 不存在，则返回空。
gets 命令的基本语法格式如下：
```
gets key
```
多个 key 使用空格隔开，如下:
```
gets key1 key2 key3
```
## 删除命令
### delete命令
Memcached delete 命令用于删除已存在的 key(键)。
```
delete key [noreply]
```
参数说明如下：
- key：键值 key-value 结构中的 key，用于查找缓存值。
- noreply（可选）： 该参数告知服务器不需要返回数据

## 高级
### Memcache 查看列出所有key方法
```
stats items          // 列出所有keys
stats cachedump 7 0  // 通过itemid获取key
//列出的items id，本例中为7，第2个参数为列出的长度，0为全部列出
get key             //通过get获取key值
```

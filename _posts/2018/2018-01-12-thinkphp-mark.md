---
layout: post
title: thinkphp 知识点备忘录
categories:  thinkphp
tags:  thinkphp
---

* content
{:toc}

### 模版中（view）获取cookies
```html
  //html
  {$Think.cookie.think_language}
  //javascript
  console.log('{$Think.cookie.think_language}');
```




### 获取系统变量[^1]

| 用法              | 含义          | 例子                                       |
| --------------- | ----------- | ---------------------------------------- |
| $Think.server   | 获取$_SERVER  | {$Think.server.php_self}                 |
| $Think.get      | 获取$_GET     | {$Think.get.id}                          |
| $Think.post     | 获取$_POST    | {$Think.post.name}                       |
| $Think.request  | 获取$_REQUEST | {$Think.request.user_id}                 |
| $Think.cookie   | 获取$_COOKIE  | {$Think.cookie.username}                 |
| $Think.session  | 获取$_SESSION | {$Think.session.user_id}                 |
| $Think.config   | 获取系统配置参数    | {$Think.config.app_status}               |
| $Think.lang     | 获取系统语言变量    | {$Think.lang.user_type}                  |
| $Think.const    | 获取系统常量      | {$Think.const.app_name}或{$Think.APP_NAME} |
| $Think.env      | 获取环境变量      | {$Think.env.HOSTNAME}                    |
| $Think.version  | 获取框架版本号     | {$Think.version}                         |
| $Think.now      | 获取当前时间      | {$Think.now}                             |
| $Think.template | 获取当前模板      | {$Think.template}                        |

### 参考资料

[^1]: [系统变量](http://doc.thinkphp.cn/manual/system_var.html)

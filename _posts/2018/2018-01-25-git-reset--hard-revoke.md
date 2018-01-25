---
layout: post
title:  执行了git reset --hard xxxxxx 后如何撤销
categories:  git
tags:  git
---

* content
{:toc}


## 前提  

如果你没有commit你的本地修改（甚至于你都没有通过git add追踪过这些文件)，git reset --hard命令对这些修改来说就是毁灭性的！！那么，下面的操作就不再适用！！！  

## 操作
1. `git fsck --lost-found`    
![](/assets/images/20180125001.png)  
或者在.git/lost-found目录下查找

2.  `git reset 14cc57ad6ef810d010d9d44b748119002254c793`  
![](/assets/images/20180125002.png)

3. `git status`  
![](/assets/images/20180125003.png)

4. `git checkout app.js ../express-generator/app.js`  
![](/assets/images/20180125004.png)

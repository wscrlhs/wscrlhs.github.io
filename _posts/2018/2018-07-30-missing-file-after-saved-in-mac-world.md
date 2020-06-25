---
layout: post
title: mac word 保存后内容丢失
categories: [mac]
tags:
  - mac 
---


## 泪奔
想死了心都有了，今天下午辛辛苦苦写了几千字的我word文档，保存后竟然丢失了。
我十分确定自己保存了，可是打开文件后竟然是一片空白。难道又要重新做一遍？内心xx苹果n次。。。

## 然并卵
没办法，赶紧百度一下
找到微软的一篇文章[恢复 for Mac 的 Office 中的文件](https://support.office.com/zh-cn/article/%E6%81%A2%E5%A4%8D-for-mac-%E7%9A%84-office-%E4%B8%AD%E7%9A%84%E6%96%87%E4%BB%B6-6c6425b1-6559-4bbf-8f80-4f038402ff02?ocmsassetID=HA102927241&CorrelationId=156f05fa-b765-43f3-a57b-61ccaf8e155d&ui=zh-CN&rs=zh-CN&ad=CN),然并卵，我的AutoRecovery 文件夹下一片空白。
再找一找万能的小伙伴们，果然有很多同病相怜的病友们。

## 喜极而泣
万万没想到，竟然在神奇的**百度贴吧**中找到了解决方法,这大大改变了我对贴吧的印象(*^__^*).
- 打开终端，输入sudo find / -name "你丢失的文件名.tmp"
- 然后你就会找到在/private/var/folders/下，然后有的人是/g9，我的是k6，就是找到一个T 文件夹下有名字叫com.microsoft.Word 的文件夹，再在这个文件夹或更深层文件夹找到有.tmp的文件
- 把这个文件拷贝出来，重命名后缀位.docx,这个就是丢失的文件



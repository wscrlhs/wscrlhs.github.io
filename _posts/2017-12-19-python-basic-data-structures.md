---
layout: post
title: Python基础之数据结构
categories: Python
tags: Python
---

* content
{:toc}

## 数据结构
>**列表，字典，元组，集合**

```python
val1 = 1
val2 =2
val3 =3
val4 =4
key1 = 'a'
key2 = 'b'
list = [val1,val2,val3,val4]
dict = {key1:val2,key2:val2}
tuple = (val1,val2,val3,val4)
set = {val1,val2,val3,val4}
```




### 列表(list)
- 列表中的每个元素都是可变的
- 列表中的元素是有序的，也就是说每一个元素都有一个位置
- 列表中可用容纳Python的任何对象
列表的元素是可变的，意味着我们可以在列表中添加、删除和修改元素
列表中的元素是有序的，我们通过输入位置查询该位置所对应的值

```python
weekday = ['monday','tuesday','wednesday','thursdaya','friday']
print(weekday[0])

all_in_list = [
  1, #整数
  1.0,#浮点数
  'a word',#字符
  print(1),#函数
  True,#布尔型
  [1,2],#列表
  (1,2),#元组
  {'key':'value'},#字典
    ]

# 插入
fruit = ['pineapple','pear']
fruit.insert(1,'grape')
fruit[0:0] = ['orange']

#删除
fruit.remove('pear')
del fruit[0:2]

#修改
fruit[0] = 'grapefruit'
```

### 字典(dictionary)
- 字典中的数据必须以键值对的形式出现
- 逻辑上讲，键是不能重复的，而值可以重复
- 字典中的键（key）是不可变的，也就是无法修改，而值是可变的，可以修改，可以是任何对象

```python
code = {
'bidu':'baidu',
'sina':'sina',
'yoku':'youku'
}

#添加
code['yoku'] = 'youku'
code.update({'fb':'facebook','tsla':'tesla'})

#删除
del code['fb']
```

### 元组(tuple)
- 可以理解成一个稳固版的列表，因为元组是不可修改的

```python
letters = ('a','b','c','d','f')
letters[0]
```

### 集合(set)
- 每个集合的元素是无序的、不重复的任意对象.
- 所以数组不能被切片也不能被索引，除了做集合运算，还可以被添加和删除

```python
a_set = {1,2,3}
a_set.add(4)
a_set.discard(4)
```


## 推导式
>list = [item for item in iterable]

```python
a = []
for i in range(1,11):
    a.append(i)

#可以写成下列方式
b = [i for i in range(1,11)]
```

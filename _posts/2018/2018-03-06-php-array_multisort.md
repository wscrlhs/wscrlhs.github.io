---
layout: post
title:  PHP数组排序array_multisort函数详解
categories:  php
tags:  php
---

* content
{:toc}

## 定义和用法  
array_multisort()可以用来一次对多个数组进行排序，或者根据某一维或多维对多维数组进行排序。 

注释：字符串键名将被保留，但是数字键名将被重新索引，从 0 开始，并以 1 递增。

注释：您可以在每个数组后设置排序顺序和排序类型参数。如果没有设置，每个数组参数会使用默认值。


## 语法  
```php
array_multisort(array1[,sorting order[,sorting type]]
[,array2[,sorting order[,sorting type]]]
[,array3]...)
```





| 参数              | 描述                                       |
| :-------------- | :--------------------------------------- |
| *array1*        | 必需。规定数组。                                 |
| *sorting order* | 可选。规定排列顺序。可能的值：<br> - SORT_ASC - 默认。按升序排列 (A-Z)。<br> - SORT_DESC - 按降序排列 (Z-A)。 |
| *sorting type*  | 可选。规定排序类型。可能的值：<br> - SORT_REGULAR - 默认。把每一项按常规顺序排列（Standard ASCII，不改变类型）。<br> - SORT_NUMERIC - 把每一项作为数字来处理。<br> - SORT_STRING - 把每一项作为字符串来处理。<br> - SORT_LOCALE_STRING - 把每一项作为字符串来处理，基于当前区域设置（可通过 setlocale() 进行更改）。<br> - SORT_NATURAL - 把每一项作为字符串来处理，使用类似 natsort() 的自然排序。<br> - SORT_FLAG_CASE - 可以结合（按位或）SORT_STRING 或 SORT_NATURAL 对字符串进行排序，不区分大小写。 |
| *array2*        | 可选。规定数组。                                 |
| *array3*        | 可选。规定数组。                                 |

## 实例  
### 对多个数组排序  
```php
$ar1 = array(10, 100, 100, 0);
$ar2 = array(1, 3, 2, 4);
//排序后，第一个数组会包含 0、 10、 100、 100。 第二个数组会包含 4、1、 2、 3。 第二个数组里的项目对应第一个数组后也进行了排序（100 和 100）。
array_multisort($ar1, $ar2);

var_dump($ar1);
var_dump($ar2);

//output:
array (size=4)
  0 => int 0
  1 => int 10
  2 => int 100
  3 => int 100
array (size=4)
  0 => int 4
  1 => int 1
  2 => int 2
  3 => int 3
```
### 排序多维数组  
```php
$ar = array(
array("10", 11, 100, 100, "a"),
array(   1,  2, "2",   3,   1)
);

//排序后，第一个数组将变成 "10"，100，100，11，"a"（被当作字符串以升序排列）。第二个数组将包含 1, 3, "2", 2, 1（被当作数字以降序排列）。
array_multisort($ar[0], SORT_ASC, SORT_STRING,
$ar[1], SORT_NUMERIC, SORT_DESC);
var_dump($ar);

//output:
array (size=2)
  0 =>
    array (size=5)
      0 => string '10' (length=2)
      1 => int 100
      2 => int 100
      3 => int 11
      4 => string 'a' (length=1)
  1 =>
    array (size=5)
      0 => int 1
      1 => int 3
      2 => string '2' (length=1)
      3 => int 2
      4 => int 1
```

### 根据某列对多位数组排序  
```php
$arr = array(
    array(
        'top' => 0,
        'cnt' => 20,
        'message' => '第一组数',
    ),
    array(
        'top' => 0,
        'cnt' => 10,
        'message' => '第二组数',
    ), array(
        'top' => 1,
        'cnt' => 30,
        'message' => '第三组数',
    ),
    array(
        'top' => 1,
        'cnt' => 40,
        'message' => '第四组数',
    )
);

//先根据top列按照降序排序，如果值相同再按照cnt列升序排序
array_multisort(array_column($arr, 'top'), SORT_DESC, SORT_NUMERIC,
    array_column($arr, 'cnt'), SORT_ASC, SORT_NUMERIC,
    $arr);
var_dump($arr);

//output:
array (size=4)
  0 =>
    array (size=3)
      'top' => int 1
      'cnt' => int 30
      'message' => string '第三组数' (length=12)
  1 =>
    array (size=3)
      'top' => int 1
      'cnt' => int 40
      'message' => string '第四组数' (length=12)
  2 =>
    array (size=3)
      'top' => int 0
      'cnt' => int 10
      'message' => string '第二组数' (length=12)
  3 =>
    array (size=3)
      'top' => int 0
      'cnt' => int 20
      'message' => string '第一组数' (length=12)
```

## 参考  
[PHP array_multisort() 函数](http://www.w3school.com.cn/php/func_array_multisort.asp)  
[PHP: array_multisort - Manual](http://php.net/manual/zh/function.array-multisort.php)  

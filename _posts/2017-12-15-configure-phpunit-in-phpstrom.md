---
layout: post
title:  在PhpStrom中配置使用PHPUnit
categories:  PHPUnit PhpStrom
tags:  PHPUnit PhpStrom
---

* content
{:toc}

## 环境
PhpStrom 2017.2.2

PHP 5.6.31

## 下载phpunit.phar依赖库
根据PHP版本下载相应的PHPUnit档案包phpunit.phar

![](http://ww1.sinaimg.cn/mw690/73f02bfcgy1fmhp13boh4j20yk06zmxn.jpg)

下载地址:
[https://phar.phpunit.de/](https://phar.phpunit.de/)




## 配置phpunit
File->Default Settings->Languages & Frameworks->PHP->Test Frameworks,点击+添加

![](http://ww1.sinaimg.cn/large/73f02bfcgy1fmhpez0ipyj20st0jldht.jpg)

## 添加依赖库
项目下External Libraries右键选择Configure PHP Include Paths...

![](http://ww1.sinaimg.cn/large/73f02bfcgy1fmhpl0lngkj20an06swef.jpg)

选择你刚才下载的phpunit.phar

![](http://ww1.sinaimg.cn/large/73f02bfcgy1fmhpndwnl8j20ew0k7gmq.jpg)

## 编写测试用例
- Code

src/Email.php

```php
<?php


final class Email
{
    private $email;

    private function __construct($email)
    {
        $this->ensureIsValidEmail($email);

        $this->email = $email;
    }

    public static function fromString($email)
    {
        return new self($email);
    }

    public function __toString()
    {
        return $this->email;
    }

    private function ensureIsValidEmail($email)
    {
        if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
            throw new InvalidArgumentException(
                sprintf(
                    '"%s" is not a valid email address',
                    $email
                )
            );
        }
    }
}
```
- Test Code

tests/EmailTest.php

```php
<?php


use PHPUnit\Framework\TestCase;

/**
 * @covers Email
 */
final class EmailTest extends TestCase
{
    public function testCanBeCreatedFromValidEmailAddress()
    {
        $this->assertInstanceOf(
            Email::class,
            Email::fromString('user@example.com')
        );
    }

    public function testCannotBeCreatedFromInvalidEmailAddress()
    {
        $this->expectException(InvalidArgumentException::class);

        Email::fromString('invalid');
    }

    public function testCanBeUsedAsString()
    {
        $this->assertEquals(
            'user@example.com',
            Email::fromString('user@example.com')
        );
    }
}
```

- Test Execution

```php
➜ phpunit --bootstrap src/Email.php tests/EmailTest
PHPUnit 6.5.0 by Sebastian Bergmann and contributors.

...                                                                 3 / 3 (100%)

Time: 70 ms, Memory: 10.00MB

OK (3 tests, 3 assertions)
```
## 参考
[PHPUnit中文手册](https://phpunit.de/manual/current/zh_cn/installation.html)


---
title: php 文件锁的简单实现
data: 2017-07-01 3:24
categories: php
tags: lock 并发
---
### 文件锁是什么
[**flock**](http://php.net/manual/zh/function.flock.php)轻便的咨询文件锁定


### 为什么要用文件锁

对于日IP不高或者说并发数不是很大的应用，一般不用考虑这些！用一般的文件操作方法完全没有问题。但如果并发高，在我们对文件进行读写操作时，很有可能多个进程对进一文件进行操作，如果这时不对文件的访问进行相应的独占，就容易造成数据丢失。

### 怎么用文件锁

- LOCK_SH取得共享锁定（读取的程序）。
- LOCK_EX 取得独占锁定（写入的程序。
- LOCK_UN 释放锁定（无论共享或独占）。

> 如果不希望 flock() 在锁定时堵塞，则是 LOCK_NB

``` php  

    $fp = fopen('file.txt', 'r');

    if(flock($fp, LOCK_EX | LOCK_NB)){
        //do something
        echo '锁获取成功';
        flock($fp, LOCK_UN);
    } else {
        echo '系统繁忙';    
    }

```
### 文件锁处理高并发出现的问题
多并发情况下，经常锁文件独占资源，不释放造成死锁，从而使CPU占用过高
#### 解决方案
超时设置为1ms，如果这里时间内没有获得锁，就反复获得，直接获得到对文件操作权为止，当然。如果超时限制已到，就必需马上退出，让出锁让其它进程来进行操作。

``` php

    $fp = fopen('lock.txt', 'a');
    $start = microtime();

    do {
        $get = flock($fp, LOCK_EX); 
        if(!$get) {
            usleep(round(0, 100)*10000));
        }
    } while ((!$get) && (microtime()-$start < 1000));
    // get flock then do something
    fclose($fp);

```







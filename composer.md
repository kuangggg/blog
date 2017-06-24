---
title: composer
date: 2017-06-24 08:55:23
tags:
---
### 下载 [composer.phar](https://getcomposer.org/composer.phar)


### 新建 composer.bat 文件

` @php "%~dp0composer.phar" %*`

### 将两个文件置于同一文件夹下面，添加到环境变量中,我的添加在PHP文件夹中 xampp/php/

### 指向中国全量镜像
`composer config -g repo.packagist composer https://packagist.phpcomposer.com`

### 查看全局配置 

`composer config -gl repo.packagist`
---
title: npm
date: 2017-06-25 16:11:44
categories: js
tags: npm
---

## npm 是什么
[**npm**](https://docs.npmjs.com/)（node package manager）是**nodejs**的包管理器，用于node插件管理（包括安装、卸载、管理依赖等）
## 使用 npm 安装插件
	npm install <name> [-g] [--save-dev]
`-g`：全局安装。
将会安装在C:\Users\Administrator\AppData\Roaming\npm，并且写入系统环境变量； 非全局安装：将会安装在当前定位目录； 全局安装可以通过命令行在任何地方调用它，本地安装将安装在定位目录的node_modules文件夹下，通过require()调用；

`--save`：将保存配置信息至package.json（package.json是nodejs项目配置文件）；

`-dev`：保存至package.json的devDependencies节点，不指定-dev将保存至dependencies节点；
> 为什么要保存至package.json？因为node插件包相对来说非常庞大，所以不加入版本管理，将配置信息写入package.json并将其加入版本管理，其他开发者对应下载即可（命令提示符执行npm install，则会根据package.json下载所有需要的包）

## 卸载 npm 插件
	npm uninstall <name> [-g] [--save-dev]
## 更新 npm 插件
	npm update <name> [-g] [--save-dev]
## 更新全部插件
	npm update [--save-dev]
## 查看已安装插件
	npm list



### 使用 cnpm
	npm install cnpm -g --registry=https://registry.npm.taobao.org
> npm 默认从 [http://registry.npmjs.org](http://registry.npmjs.org) 下载插件，国外网站经常异常所以指定淘宝的插件镜像

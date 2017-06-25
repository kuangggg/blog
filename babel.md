---
title: babel
date: 2017-06-25 22:55:23
categories: js
tags: [babel, es6]
---

参考 [Babel 入门教程](http://www.ruanyifeng.com/blog/2016/01/babel.html)  [http://babeljs.io/](http://babeljs.io/)
## babel 是什么
Babel是一个广泛使用的转码器，可以将ES6代码转为ES5代码，从而在现有环境执行。
## 配置.babelrc 文件

该文件用来设置转码规则和插件，放置在根目录下，格式如下

    {
        "presets": [
          "es2015",
          "stage-2"
        ],
        "plugins": []
    }
presets字段设定转码规则根据需要添加，这里只添加 es2015 和 stage-2

## 使用命令行工具 **babel-cli** 转码
> 此处将 babel-cli 安装到项目目录下，解决了项目对全局环境的依赖

    cnpm install --save-dev babel-cli

### 修改 package.json 文件
    {
      "devDependencies": {
        "babel-cli": "^6.24.1",
        "babel-preset-es2015": "^6.24.1",
        "babel-preset-stage-0": "^6.24.1"
      },
      "scripts": {
        //配置脚本执行，以及输入输出目录
        "build": "babel src -d lib"
      }
    }

执行 `npm run build`

## babel-node
随 babel-cli 安装，命令行执行 `babel-node` 就进入PEPL环境

## babel-polyfill
Babel默认只转换新的JavaScript句法（syntax），而不转换新的API，比如Iterator、Generator、Set、Maps、Proxy、Reflect、Symbol、Promise等全局对象，以及一些定义在全局对象上的方法（比如Object.assign）都不会转码。

    cnpm install --save babel-polyfill
使用

    import 'babel-polyfill';
    // 或者
    require('babel-polyfill');

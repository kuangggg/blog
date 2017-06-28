---
title: ES6 数组遍历 for-of
date: 2017-06-28 17:35:23
categories: js
tags: [js, es6]
---

## 数组循环常规写法

``` javascript

    var arr = [1, 2, 3, 4];
    for(var i=0; i<arr.length; i++) {
        console.log(arr[i]);
    }

```
## 常见 for-in 错误迭代数组

``` javascript

    Array.prototype.method = function() {
        console.log(this.length);
    }
    arr.name = 'my array';
    let arr = [1, 2, 8,3, 6, 7];
    for(var i in arr) {
        console.log(arr[i]);
    }

```
- 代码中的下标 **i** 是字符串并不是真正的数字
- for-in 除了遍历数组元素外，还会遍历所可枚举属性，包括原型链上的属性
- 某些情况遍历顺序随机
- for-in是为普通对象设计的，你可以遍历得到字符串类型的键，因此不适用于数组遍历

## ES5之后 数组对象使用内置的 **forEach** 方法

``` javascript

    arr.forEach(function(value){
        console.log(value);
    });

```
> 无法用 *break*  *return* 语句终止

## 强大的 for-of 循环

``` javascript

    for(var v of arr) {
        console.log(v);
    }

```
TBD

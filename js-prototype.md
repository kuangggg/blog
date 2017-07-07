




## 前言
关于 `__proto__ prototype constructor` 的概念，网上有太多说辞，有些都上升到了哲学的地步，什么万物始于null,js 全是对象,鸡生蛋蛋生鸡。在我看来只是一千个读者眼中的哈姆雷特,要完全理解必须追根溯源。


## 弄清楚 js 中的数据类型

1. 原始数据类型
    - 数字
    - 字符串
    - 布尔
    - null
    - undefined
2. 对象数据类型
    - 键值对的属性集合体。

>原始值不可变，对象引用可以改变，这就反向印证了C语言中字符串和对象的内存结构。


为什么原始数据类型有属性方法呢？

只要引用字符串(数字布尔)的属性，js就会将字符串通过 new String(str) 进行转化,这个过程叫做包装对象。
这种也叫伪对象。


``` javascript

    var str = 'hello';

    p(str.length);

    var objStr = new String(str);
    p(objStr.length);

    console.log(str == objStr); //true
    console.log(str === objStr); //false  因为是不同类型

```


## js 中如何创建对象

### 使用对象直接量直接创建
对象直接量就是有键值对组成的映射表。
``` javascript

    var o = {};

```
### 使用构造函数 new 一个对象

``` javascript

    var o = new Object();

```

### ECMAScript5 创建对象

``` javascript

    //第一个参数是这个对象的原型
    var o = Object.create({a:1});

    var o = Object.create(Object.prototype);
    // 等同于 var o = {};  var o = new Object();

```
## 什么是原型

js 中每个对象(null 除外)都和另一个对象关联，这里的另一个对象就是她的原型，用来属性继承。


## 理解 constructor 和 prototype __proto__ 在构造函数创建对象中的关系












---
title: js 中的 == 与 ===
date: 2017-7-7 20:01
categories: js
---

[转自 http://javascript.ruanyifeng.com](http://javascript.ruanyifeng.com/grammar/operator.html#toc6)

## 前言
- ==相等运算符比较两个值是否相等,比较前会进行类型转化
- ===严格运算符比较两个值是否为同一个值

## 严格相等运算符
### 不同类型的值
类型不同，返回 **false**

``` javascript

    1 === "1" //false
    true === 'true' //false

```

### 同类型的原始类型值

同类型的原始类型的值(数字，字符串，布尔)

``` javascript

    1 === 0x1 //true
    NaN === NaN //false

```

### 同类型的复合类型

比较的是他们的引用地址是否相同

``` javascript

    [] === [] //false

    var o = {};
    var b = o;
    a === b;//true

```

### undefined null

undefined 和 null 与自身严格相等

``` javascript

    var a;
    var b;
    a === b;//true

```

## 相等运算符
相等运算符比较相同类型的数据时，与严格相等运算符完全一样。

比较不同类型的数据时，相等运算符会先将数据进行类型转换，然后再用严格相等运算符比较

### 原始类型的值
原始类型的数据会转化成 **数值类型**，在进行比较

``` javascript

    1 == true // 1 === 1 ture

    0 == false // 0 === 0 ture

    2 == true // 2 === 1 false

    'true' == true // Number('true') === Number(true) NaN === 1 false

    '' == false // 0 === 0 true;

```

### 对象和原始类型
对象（这里指广义的对象，包括数组和函数）与原始类型的值比较时，对象转化成原始类型的值，再进行比较。

``` javascript

    [1] == 1 // true
    // 等同于 Number([1]) == 1

    [1] == '1' // true
    // 等同于 String([1]) == Number('1')

    [1] == true // true
    // 等同于 Number([1]) == Number(true)

```

### undefine null

undefined和null与其他类型的值比较时，结果都为false，它们互相比较时结果为true。
``` javascript

    false == null // false
    false == undefined // false

    0 == null // false
    0 == undefined // false

    undefined == null // true

```

### 相等运算符的缺点

```

    '' == '0'           // false
    // 都是字符串类型，所以不用转化类型,字符串'0'和''是绝对不相等的。
    0 == ''             // true
    0 == '0'            // true

    2 == true           // false
    2 == false          // false

    false == 'false'    // false
    false == '0'        // true

    false == undefined  // false
    false == null       // false
    null == undefined   // true

```

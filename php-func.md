# php 常用函数总结



## url 处理

### [http_build_query](http://php.net/manual/zh/function.http-build-query.php)
生成 URL-encode 之后的请求字符串
### [parse_url](http://php.net/manual/zh/function.parse-url.php)
解析一个 URL 并返回一个关联数组，包含在 URL 中出现的各种组成部分。省略 第二个常量参数，返回数组键可能有以下几种
- scheme (协议)
- host
- port
- user
- pass
- path
- query (? 之后的查询字串)
- fragment (# 之后的锚点之类散列符号)
``` php

    $url = 'http://www.example.com/path?googleguy=googley#g1';

    print_r(parse_url($url));
    // Array
    // (
    //     [scheme] => http
    //     [host] => www.example.com
    //     [path] => /path
    //     [query] => googleguy=googley
    //     [fragment] => g1
    // )

```

### [parse_str](http://php.net/manual/zh/function.parse-str.php)
将字符串解析成多个变量,如果设置了第二个变量 arr.变量将会以数组元素的形式存入到这个数组,作为替代.

``` php

    $str = "first=value&arr[]=foo+bar&arr[]=baz";
    parse_str($str);
    echo $first;  // value
    echo $arr[0]; // foo bar
    echo $arr[1]; // baz

    parse_str($str, $output);
    echo $output['first'];  // value
    echo $output['arr'][0]; // foo bar
    echo $output['arr'][1]; // baz

```

## 文件路径相关

### [pathinfo](http://php.net/manual/zh/function.pathinfo.php)
返回文件路径的信息
``` php

    $path = pathinfo('/demo/test.php');
    p($path);
    // Array
    // (
    //     [dirname] => /demo
    //     [basename] => test.php
    //     [extension] => php
    //     [filename] => test
    // )

```
### [basename](http://php.net/manual/zh/function.basename.php)
返回路径中的文件名部分

``` php

    $file = basename('/demo/test.php');
    $name = basename('/demo/test.php', '.php'); //如果文件名同 第二个参数相同也会被去掉

    echo $file, '<br/>', $name;
    // test.php
    // test

```

### [dirname](http://php.net/manual/zh/function.dirname.php)
返回路径中的目录部分

## 字符串相关



## 数组相关


## 正则

## To be continued




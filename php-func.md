

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

## 函数处理 函数
### [function_exists](http://php.net/manual/zh/function.function-exists.php)
函数是否定义，包括用户自定义函数。
### [call_user_func_array](http://php.net/manual/zh/function.call-user-func-array.php)
把第一个参数作为回调函数，第二个参数作为回调函数的参数，以数组形式传入传入
``` php

    function call1($param1, $param2)
    {
        echo $param1, '&',$param2;
    }

    call_user_func_array('call1', [1, 2]);
    //1&2

    class Test
    {
        function call1($p1, $p2)
        {
            echo __FUNCTION__, '&', $p1, '&', $p2;
        }

        static function call2($p1, $p2)
        {
            echo __FUNCTION__, '&', $p1, '&', $p2;
        }
    }

    $test = new Test();
    call_user_func_array([$test, "call1"], [1, 2]);
    //call1&1&2

    call_user_func_array(['Test', 'call2'], [1, 2]);
    //call2&1&2


```
### [call_user_func](http://php.net/manual/zh/function.call-user-func.php)
> 同 **call_user_func_array** 差不多，只是除过第一个参数是回调函数，其余都是参数,
> 对于只有一个参数的回调或者没有参数的回调使用比较合适
### [func_get_args](http://php.net/manual/zh/function.func-get-args.php)
返回函数参数列表的数组
``` php

    function test()
    {
        p(func_get_args());
    }

    test('test', '1');
    // Array
    // (
    //     [0] => test
    //     [1] => 1
    // )

```
### [func_num_args](http://php.net/manual/zh/function.func-num-args.php)
获取函数传入参数数目
### [func_get_arg](http://php.net/manual/zh/function.func-get-arg.php)
获取参数列表某一项
```php

    function test()
    {
        $list = func_get_args();
        for($i = 0; $i < func_num_args(); $i++) {
            echo '[', $i, '] => ', func_get_arg($i), '<br/>';
        }
    }
    test('p1', 'p2', 3);
    // [0] => p1
    // [1] => p2
    // [2] => 3

```


## 杂项
### [extension_loaded](http://php.net/manual/zh/function.extension-loaded.php)
检查一个扩展是否已经加载
```php

    if(!extension_loaded('mbstring')) {
        //不能用mb_strlen()计算中文字串长度
    }

```



## To be continued




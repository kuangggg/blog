
> 不积跬步无以至千里
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





## 字符串相关
### [strtolower](http://php.net/manual/zh/function.strtolower.php)/[strtoupper](http://php.net/manual/zh/function.strtoupper.php)/[ucfirst](http://php.net/manual/zh/function.ucfirst.php)/[ucwords](http://php.net/manual/zh/function.ucwords.php)
字符串全部字符转化为小写/大写/字符串首字母转化为大写/将字符串中每个单词的首字母转换为大写
``` php

    $str = 'hello woLd Vue';
    echo strtolower($str), '<br/>';
    echo strtoupper($str), '<br/>';
    echo ucwords($str), '<br/>';
    echo ucfirst($str);

    // hello wold vue
    // HELLO WOLD VUE
    // Hello WoLd Vue
    // Hello woLd Vue

```
### [strlen](http://php.net/manual/zh/function.strlen.php)/[mb_strlen](http://php.net/manual/zh/function.mb-strlen.php)
``` php

    $str = 'hello 中国';
    //utf-8 编码一个字符三个字节
    echo strlen($str), '<br/>';
    echo mb_strlen($str);
    // 12
    // 8

```

### [str_split](http://php.net/manual/zh/function.str-split.php)/[explode](http://php.net/manual/zh/function.explode.php)
将字符串按指定长度切割成数组/按照分隔符切分字符串成数组
``` php

    $str = 'hello';

    p(str_split($str));
    // Array
    // (
    //     [0] => h
    //     [1] => e
    //     [2] => l
    //     [3] => l
    //     [4] => o
    // )
    p(str_split($str, 2));
    // Array
    // (
    //     [0] => he
    //     [1] => ll
    //     [2] => o
    // )

```

### [strpos](http://php.net/manual/zh/function.strpos.php)/[stripos](http://php.net/manual/zh/function.stripos.php)/[strrpos](http://php.net/manual/zh/function.strrpos.php)

查找字符串首次出现的位置/最后一次出现位置/忽略大小写

``` php

    $str = 'good good study, day day up';

    var_dump(strpos($str, 'good') == false);
    var_dump(strpos($str, 'good') == 0);
    var_dump(strpos($str, 'good') === false);
    // bool(true) bool(true) bool(false) 

```

### [substr](http://php.net/manual/zh/function.substr.php)
返回字符串的字串
``` php

    $str = 'hello world';

    p(substr($str, 6)); //world
    p(substr($str, 6, 2)); //wo
    p(substr($str, -1)); //d
    p(substr($str, -2, 1)); //l

```
### [substr_replace](http://php.net/manual/zh/function.substr-replace.php)
替换字符串的字串
``` php

    $str = 'hello world';

    p(substr_replace($str, 'php', 6)); 
    p(substr_replace($str, '&', 5, 1));

    // hello php
    // hello&world

```

### [sprintf](http://php.net/manual/zh/function.sprintf.php)
返回格式化的字符串

- %b 二进制
- %c ASCII 字符
- %f 浮点型
- %s 字符串
- %o 八进制
- %x 十六进制
- %d 十进制
- %% 百分号

``` php

    $str = sprintf('%s, %f, %.2f, %c', 'abcd', 12, 12.2345, 64);

    p($str);
    // abcd, 12.000000, 12.23, @

```

### [htmlentities](http://php.net/manual/zh/function.htmlentities.php)
将所有可以转化 html 实体符号的都转化

### [htmlspecialchars](http://php.net/manual/zh/function.htmlspecialchars.php)
将特殊字符转换为 HTML 实体
- `& &amp;`
- `" &quot;`
- `' &apos;`
- `< &lt;`
- `> &gt`;
``` php

    $str='<a href="test.html">\'测试页面©\'</a><script>alert(213)</script>'; 

    //并没有转义单引号,直接执行脚本
    p($str);
    //过滤
    p(htmlentities($str));
    p(htmlspecialchars($str));
    //单引号也转义
    p(htmlentities($str, ENT_QUOTES, 'UTF-8'));

```
### [strip_tags](http://php.net/manual/zh/function.strip-tags.php)
从字符串中去除 HTML 和 PHP 标记
``` php

    $text = '<p>Test paragraph.</p><!-- Comment --> <a href="#fragment">Other text</a>';

    p(strip_tags($text));  
    p(strip_tags($text, '<p><a>'));

    // Test paragraph. Other text
    // Test paragraph.

```
### [trim](http://php.net/manual/zh/function.trim.php)/[rtrim](http://php.net/manual/zh/function.rtrim.php)/[ltrim](http://php.net/manual/zh/function.ltrim.php)
去除空白符
### [str_shuffle](http://php.net/manual/zh/function.str-shuffle.php)
随机打乱一个字符串
``` php

    $str = 'abcdef';
    str_shuffle($str);

```
### [strrev](http://php.net/manual/zh/function.strrev.php)
翻转字符串


## 数组相关


## 正则
### [preg_split](http://php.net/manual/zh/function.preg-split.php)
正则匹配分割字符串
``` php

    $str = "hello world\t  prge";
    $arr = preg_split('/[\s,]+/', $str);
    p($arr);
    // Array
    // (
    //     [0] => hello
    //     [1] => world
    //     [2] => prge
    // )

```php


## 函数处理

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
## 文件相关

### [file](http://php.net/manual/zh/function.file.php)
将文件读入到数组中
``` php

    p(file('demo1.txt'));
    //在数组每个元素的末尾不要添加换行符  / 跳过空行
    p(file('demo1.txt',  FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES));

```

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

## 杂项
### [extension_loaded](http://php.net/manual/zh/function.extension-loaded.php)
检查一个扩展是否已经加载
```php

    if(!extension_loaded('mbstring')) {
        //不能用mb_strlen()计算中文字串长度
    }

```



## To be continued




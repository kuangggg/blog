## 什么是索引

索引是一种特殊的文件(InnoDB数据表上的索引是表空间的一个组成部分)，它们包含着对数据表里所有记录的引用指针。更通俗的说，数据库索引好比是一本书前面的目录，能加快数据库的查询速度。

## 索引类型

### 普通索引

这是最基本的索引，它没有任何限制

``` mysql

    -- 直接创建索引
    create index [index_name] on [tb_name(column(len))];

    -- 修改表结构，添加索引
    alter table [tb_name] add index [index_name] [(column(len))]
    
    -- 创建表的时候直接创建索引
    create table [tb_name] (
        
        index [index_name] (col(length))
        );

    -- 删除索引
    drop index [index_name] on [tb_name];

```

### 唯一索引

列的值必须唯一，可以为空 ** 主键不能不能为空 **,

``` mysql

    -- 创建唯一索引
    create unique index [index_name] on [tb_name(column(len))];

    -- 修改表结构，添加索引
    alter table [tb_name] add unique [index_name] [(column(len))]
    
    -- 创建表的时候直接创建索引
    create table [tb_name] (
        
        unique [index_name] (col(length))
        );

```

### 主键索引
特殊的唯一索引，不允许为空值。只能有一个，建表的同时创建


### 联合索引

``` mysql

    create table [tb_name] (
        index [index_name] (col1, col2)
        );

```



### 全文索引
TBD

``` mysql

    -- 直接创建全文索引
    create fulltext index [index_name] on [tb_name(col)];
    -- 修改结构添加全文索引
    alter table [tb_name] add fulltext [index_name(column(len))]
    -- 创建添加
    create tabel [tb_name](
        fulltext (col)
        );



```

## 索引的优点

1.可以通过建立唯一索引或者主键索引,保证数据库表中每一行数据的唯一性.
2.建立索引可以大大提高检索的数据,以及减少表的检索行数
3.在表连接的连接条件 可以加速表与表直接的相连
4.在分组和排序字句进行数据检索,可以减少查询时间中 分组 和 排序时所消耗的时间(数据库的记录会重新排序)
5.建立索引,在查询中使用索引 可以提高性能

## 索引的缺点

1.在创建索引和维护索引 会耗费时间,随着数据量的增加而增加
2.索引文件会占用物理空间,除了数据表需要占用物理空间之外,每一个索引还会占用一定的物理空间
3.当对表的数据进行 INSERT,UPDATE,DELETE 的时候,索引也要动态的维护,这样就会降低数据的维护速度,(建立索引会占用磁盘空间的索引文件。一般情况这个问题不太严重，但如果你在一个大表上创建了多种组合索引，索引文件的会膨胀很快)

## 尝试建立索引
1.在经常需要搜索的列上,可以加快索引的速度
2.主键列上可以确保列的唯一性
3.在表与表的而连接条件上加上索引,可以加快连接查询的速度
4.在经常需要排序(order by),分组(group by)和的distinct 列上加索引 可以加快排序查询的时间,  (单独order by 用不了索引，索引考虑加where 或加limit)
5.在一些where 之后的 < <= > >= BETWEEN IN 以及某个情况下的like 建立字段的索引(B-TREE)
6.like语句的 如果你对nickname字段建立了一个索引.当查询的时候的语句是 nickname lick '%ABC%' 那么这个索引讲不会起到作用.而nickname lick 'ABC%' 那么将可以用到索引
7.索引不会包含NULL列,如果列中包含NULL值都将不会被包含在索引中,复合索引中如果有一列含有NULL值那么这个组合索引都将失效,一般需要给默认值0或者 ' '字符串
8.使用短索引,如果你的一个字段是Char(32)或者int(32),在创建索引的时候指定前缀长度 比如前10个字符 (前提是多数值是唯一的..)那么短索引可以提高查询速度,并且可以减少磁盘的空间,也可以减少I/0操作.
9.不要在列上进行运算,这样会使得mysql索引失效,也会进行全表扫描
10.选择越小的数据类型越好,因为通常越小的数据类型通常在磁盘,内存,cpu,缓存中 占用的空间很少,处理起来更快

## 糟糕的尝试

1.查询中很少使用到的列 不应该创建索引,如果建立了索引然而还会降低mysql的性能和增大了空间需求.
2.很少数据的列也不应该建立索引,比如 一个性别字段 0或者1,在查询中,结果集的数据占了表中数据行的比例比较大,mysql需要扫描的行数很多,增加索引,并不能提高效率
3.定义为text和image和bit数据类型的列不应该增加索引,
4.当表的修改(UPDATE,INSERT,DELETE)操作远远大于检索(SELECT)操作时不应该创建索引,这两个操作是互斥的关系

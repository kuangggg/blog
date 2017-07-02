---
title: 常用 sql 语句总结
date: 2017-7-1 19:13
categories: mysql
tags: sql
---

## SQL 增删改查

``` mysql

    create database [db_name];

    drop database [db_name];

    create table [tb_name] if not exists (
    );

    drop table [tb_name];


    //查询
    select [field] from [tb_name];
    //去重
    select distinct [field] from [tb_name];
    //聚合函数
    select count([field]) from [tb_name];
    select * from [tb_name] limit [num];
    //默认将 int 型转化为 Y-m-d H:i:s 格式,
    select from_unixtime(time, '%Y-%m-%d') from [tb_name];


    //批量插入
    insert into [tb_name] values (),();


    //更新
    update [tb_name] set [field] = [val];
    update [tb_name] set [field] = [val] where [field] = [val];
    update [tb_name] set [field] += [field];


    //删除表
    delete from [tb_name];
    //删除记录
    delete from [tb_name] where [];

    
    //排序
    select * from [tb_name] order by [field] [ASC [DESC]]

    //分组
    select * from [tb_name] group by [field]

    //left join/innder join/right join
    select [a.fields] from [tb_name] as a left join select [b.fields] on a.field = b.field

```


## SQL 修改表结构

> 尽量在表设计之初就确定好结构，修改是下下策

``` mysql

    //删除列
    alter table [tb_name] drop [field]
    //增加列
    alter table [tb_name] add [mail int not null comment '增加的列'];
    //修改列的类型信息
    alter table [tb_name] change [old_field] [mail int not null comment '新修改的列']
    //删除主键
    alter table [tb_name] drop primary key

```


## 表导入导出

``` shell

    //导入
    mysql -uroot -pfanhougame --default-character-set=utf8 collect_data < collect_data.sql

    // -d 只导出表结构
    mysqldump -uroot -pfanhougame -d statistic_data > /tmp/statistic_data.sql

```

## 杂项

``` mysql

    //查询负载过高语句
    show process
    
```
``` mysql

    //分析sql执行
    explain [sql]

```
- table：显示这一行的数据是关于哪张表的
- type：这是重要的列，显示连接使用了何种类型。从最好到最差的连接类型为const、eq_reg、ref、range、 indexhe和ALL
- possible_keys：显示可能应用在这张表中的索引。如果为空，没有可能的索引。可以为相关的域从WHERE语句中选择一个合适的语句
- key： 实际使用的索引。如果为NULL，则没有使用索引。很少的情况下，MYSQL会选择优化不足的索引。这种情况下，可以在SELECT语句中使用USE         INDEX（indexname）来强制使用一个索引或者用IGNORE INDEX（indexname）来强制MYSQL忽略索引
- key_len：使用的索引的长度。在不损失精确性的情况下，长度越短越好
- ref：显示索引的哪一列被使用了，如果可能的话，是一个常数
- rows：MYSQL认为必须检查的用来返回请求数据的行数
- Extra：关于MYSQL如何解析查询的额外信息。坏的例子是Using temporary和Using filesort，意思MYSQL根本不能使用索引，结果是检索会很慢




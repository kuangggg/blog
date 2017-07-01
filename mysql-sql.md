---
title: 常用 sql 语句总结
date: 2017-7-1 19:13
categories: mysql
tags: sql
---

## SQL 增删改查

``` shell

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

``` shell

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

``` shell

    //查询负载过高语句
    show process

    //分析sql执行
    explain [sql]  

```



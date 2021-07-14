#### DDL操作



##### 库操作

```mysql
create database 数据库名;   #直接创建数据库，存在则报错
create database if not exists 数据库名;		#如果不存在则创建
create database 数据库名 character set 字符集;	#创建时设置字符集

drop database 数据库名；  #删库

use 数据库名;  #选中该数据库
select database();  #查看正在使用的数据库
```



##### 表操作

```mysql
#创建表
create table if not exists 表名(
字段名 类型(长度)[约束],
字段名 类型(长度)[约束],
    ····
);
类型：
	varchar(n) 字符串
	int	整形
	double 浮点
	date 时间
	timestamp 时间戳
约束：
primary key 主键，被主键修饰字段中的数据，不能重复，不能为null
auto_increment 自动增长，只能用于数字

#实例
create table category(
    cid varchar(20)primary key ,
    cname varchar(100)
);

#查看表
show tables;
desc category;

#删表
drop table 表名;
```


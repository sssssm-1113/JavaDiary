#### DQL操作



##### 语法

```mysql
select [distinct]
* | 列名,列名
from 表
where 条件
```



##### 基本操作

```mysql
-- 去重复值
select distinct price from product;
```



##### 排序查询

```mysql
SELECT * FROM 表名 
ORDER BY 排序字段 
ASC|DESC;
-- ASC:升序（默认）ascend
-- DESC:降序 descend
```



##### 聚合查询

| 聚合函数 | 作用                                                         |
| -------- | ------------------------------------------------------------ |
| count()  | 统计指定列不为NULL的记录行数                                 |
| sum()    | 计算指定列数值和，如果指定列不是数值类型，计算结果为0        |
| max()    | 计算指定列最大值，如果指定列是字符串类型，使用字符串排序计算 |
| min()    | 计算指定列最小值，如果指定列是字符串类型，使用字符串排序计算 |
| avg()    | 计算指定列平均值，如果指定列不是数值类型，计算结果为0        |
| ifnull() | 判断score是否为null，如果为null，则score为0<br/>   select avg(ifnull(score,0)) from stu; |

```mysql
SELECT 函数名(指定列) 
FROM 表名
```



##### 分组查询

```mysql
SELECT 字段一,字段二,...
FROM 表名
GROUP BY 分组字段
HAVING　分组条件;

-- 统计各个分类商品的个数
SELECT category_id,COUNT(*) FROM product GROUP BY category_id;
-- 统计各个分类商品的个数且只显示个数大于一的信息
SELECT category_id,COUNT(*) FROM product GROUP BY category_id HAVING COUNT(*) >1;
```

having与where的区别：

* having在分组后对数据进行过滤，where在分组前
* having后可以使用分组函数（统计函数），where后不可以使用分组函数



##### SQL语句执行顺序

<img src="C:\Users\krato\Desktop\mySQL\SQL顺序.jpg">



##### 分页查询

```mysql
SELECT　字段一,字段二,... 
FROM　表名　
LIMIT　M,N;
-- M：整数，表示从第几条索引开始  (当前的页数 - 1) *  每一页显示的条数
-- N：整数，表示查询多少条数据
```

第1页: limit 0,5
第2页: limit 5,5
第3页: limit 10,5
   ...
第10页: limit 45,5



##### insert into select 语句

把一个表需要的内容复制到另一个存在的表中
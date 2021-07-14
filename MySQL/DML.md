#### DML操作



##### 插入表记录：insert

```mysql
-- 向表中插入某些字段
insert into 表(字段一,字段二,字段三..)values(值一,值二,值三...)；
-- 向表中插入所有字段，字段的顺序为创建表时的顺序
insert into 表 values(值一,值二,值三..),(值一,值二,值三..);

insert into category(cid,cname)values('c001','电器');
insert into category(cid,cname)values('c002','手机');

```



##### 更新表记录：update

用来修改指定条件的数据，将满足条件的记录指定列修改为指定值

```mysql
-- 更新所有记录的指定字段
update 表名 set 字段名 = 值,字段名 = 值,...;
-- 更新符号条件记录的指定字段
update 表名 set 字段名 = 值,字段名 = 值,... where 条件;

#实例
update category set cname = '家电'; #讲所有行的cname改为家电
update category set cname = '水果' where cid = 'c001'; #将cid为c001的cname改为水果
```



##### 删除记录：delete

```mysql
delete from 表名 [where 条件];
truncate table 表名;

-- delete 一条一条删除，不会清空auto_increment
-- truncate 直接删表，重新建表，auto_increment将置为0，重新开始
```


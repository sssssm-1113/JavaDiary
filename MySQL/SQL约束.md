#### SQL约束



##### 1.主键约束

PRIMARY KEY：

值不能重复，不能为空，每个表中只有一个主键

```mysql
-- 主键
CREATE TABLE category(
    cid varchar(20)PRIMARY KEY ,
    cname varchar(100)
);

CREATE TABLE Person(
	FirstName varchar(255),
    LastName varchar(255),
    City varchar(255),
    # 联合主键
    CONSTRAINT keyName PRIMARY KEY(FirstName,LastName)
)

-- 自动增长列
CREATE TABLE student(
	id int PRIMARY KEY AUTO_INCREMENT
)
```



##### 2.非空约束

```mysql
CREATE TABLE student1(
	Id int  NOT NULL,
    City varchar(255) NOT NULL
)
```



##### 3.唯一约束

UNIQUE



##### 4.外键约束

FOREIGN KEY
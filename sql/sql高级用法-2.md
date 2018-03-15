---

title: SQL高级用法
date: 2018-03-15 08:30:56
tags: sql
categories: 数据库

---

###  join  

> 用于根据两个或多个表中的列之间的关系，从这些表中查询数据。

```
SELECT Persons.LastName, Persons.FirstName, Orders.OrderNo
FROM Persons, Orders
WHERE Persons.Id_P = Orders.Id_P 
```

> 使用join

```
select Persons.lastName,Persons.FirstName,Orders.orderNo
from Persons
inner join Orders
on Persons.Id_P = Orders.Id_P
order by Persons.lastName
```

> 不同的 SQL JOIN,除了我们在上面的例子中使用的 INNER JOIN（内连接），我们还可以使用其他几种连接。
下面列出了您可以使用的 JOIN 类型，以及它们之间的差异

- JOIN: 如果表中有至少一个匹配，则返回行。与inner join是相同的
- LEFT JOIN: 即使右表中没有匹配，也从左表返回所有的行
- RIGHT JOIN: 即使左表中没有匹配，也从右表返回所有的行
- FULL JOIN: 只要其中一个表中存在匹配，就返回行

### left join

> LEFT JOIN 关键字会从左表 (table_name1) 那里返回所有的行，即使在右表 (table_name2) 中没有匹配的行。

```
SELECT column_name(s)
FROM table_name1
LEFT JOIN table_name2 
ON table_name1.column_name=table_name2.column_name
```

### right join

> RIGHT JOIN 关键字会右表 (table_name2) 那里返回所有的行，即使在左表 (table_name1) 中没有匹配的行。

```
SELECT column_name(s)
FROM table_name1
RIGHT JOIN table_name2 
ON table_name1.column_name=table_name2.column_name
```


### full join

> 只要其中某个表存在匹配，FULL JOIN 关键字就会返回行。

```
SELECT column_name(s)
FROM table_name1
FULL JOIN table_name2 
ON table_name1.column_name=table_name2.column_name
```

### union 操作符

> UNION 操作符用于合并两个或多个 SELECT 语句的结果集。请注意，UNION 内部的 SELECT 语句必须拥有相同数量的列。列也必须拥有相似的数据类型。同时，每条 SELECT 语句中的列的顺序必须相同。

```
SELECT column_name(s) FROM table_name1
UNION
SELECT column_name(s) FROM table_name2
```
> 默认地，UNION 操作符选取不同的值。如果允许重复的值，请使用 UNION ALL

```
SELECT column_name(s) FROM table_name1
UNION ALL
SELECT column_name(s) FROM table_name2
```

### SELECT INTO 语句可用于创建表的备份复件

>  - SELECT INTO 语句从一个表中选取数据，然后把数据插入另一个表中。
>  - SELECT INTO 语句常用于创建表的备份复件或者用于对记录进行存档。

- 您可以把所有的列插入新表：

```
SELECT *
INTO new_table_name [IN externaldatabase] 
FROM old_tablename
```

- 或者只把希望的列插入新表：

```
SELECT column_name(s)
INTO new_table_name [IN externaldatabase] 
FROM old_tablename
```

- 下面的例子会制作 "Persons" 表的备份复件：

```
SELECT *
INTO Persons_backup
FROM Persons
```

- IN 子句可用于向另一个数据库中拷贝表：

```
SELECT *
INTO Persons IN 'Backup.mdb'
FROM Persons
```

- 如果我们希望拷贝某些域，可以在 SELECT 语句后列出这些域：

```
SELECT LastName,FirstName
INTO Persons_backup
FROM Persons
```

-  SELECT INTO 实例  带有 WHERE 子句

> 下面的例子通过从 "Persons" 表中提取居住在"Beijing" 的人的信息，创建了一个带有两个列的名为"Persons_backup" 的表：

```
SELECT LastName,Firstname
INTO Persons_backup
FROM Persons
WHERE City='Beijing'
```

- SELECT INTO 实例  被连接的表

> 下面的例子会创建一个名为 "Persons_Order_Backup" 的新表，其中包含了从 Persons 和 Orders 两个表中取得的信息：

```
SELECT Persons.LastName,Orders.OrderNo
INTO Persons_Order_Backup
FROM Persons
INNER JOIN Orders
ON Persons.Id_P=Orders.Id_P
```

### CREATE DATABASE 语句

> CREATE DATABASE 用于创建数据库。

```
CREATE DATABASE database_name
```

### CREATE TABLE 语句

> CREATE TABLE 语句用于创建数据库中的表。

```
CREATE TABLE 表名称
(
列名称1 数据类型,
列名称2 数据类型,
列名称3 数据类型,
....
)
```
---

title: SQL高级用法
date: 2018-03-15 08:20:56
tags: sql
categories: 数据库

---

### TOP 

> TOP 子句用于规定要返回的记录的数目。MYSQL中对应的是limmit m，n 即从第m+1条开始取n条记录.ORACLE中是ROWNUM < num

```
select top 5 column_name from table_name --sql
select colume_name from table_name limmit 5  --mysql
select colume_name from table_name where ROWNUM <= 5 --oracle
```

### LIKE

> LIKE 操作符用于在 WHERE 子句中搜索列中的指定模式。%代表通配符

```
select * from table_name where name like 'w%' --检索名称是w开头的
```

### 通配符

> 在搜索数据库中的数据时，SQL 通配符可以替代一个或多个字符。
SQL 通配符必须与 LIKE 运算符一起使用。在 SQL 中，可使用以下通配符

- % 替代一个或多个字符
- _ 仅替代一个字符
- [charlist] 字符列中的任何单一字符 eg:[a]
- [^charlist]或者[!charlist] 不在字符列中的任何单一字符 eg:[!a]


### IN 操作符

> IN 操作符允许我们在 WHERE 子句中规定多个值

```
SELECT column_name(s) 
FROM table_name 
WHERE column_name 
IN (value1,value2,...)
```

### BETWEEN 操作符

> BETWEEN 操作符在 WHERE 子句中使用，作用是选取介于两个值之间的数据范围

```
SELECT column_name(s)
FROM table_name
WHERE column_name
BETWEEN value1 AND value2
```
> 如需使用上面的例子显示范围之外的人，请使用 NOT 操作符：

```
SELECT * FROM Persons
WHERE LastName
NOT BETWEEN 'Adams' AND 'Carter'
```

### Alias（别名）

> 通过使用 SQL，可以为列名称和表名称指定别名（Alias）

- 表的 SQL Alias 语法

```
SELECT column_name(s)
FROM table_name
AS alias_name
```

- 列的 SQL Alias 语法

```
SELECT column_name AS alias_name
FROM table_name
```

> Alias 实例: 使用表名称别名

```
SELECT po.OrderID, p.LastName, p.FirstName
FROM Persons AS p, Product_Orders AS po
WHERE p.LastName='Adams' AND p.FirstName='John'
```

> Alias 实例: 使用一个列名别名

```
SELECT LastName AS Family, FirstName AS Name
FROM Persons
```
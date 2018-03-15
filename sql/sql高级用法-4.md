---

title: SQL高级用法
date: 2018-03-15 11:30:56
tags: sql
categories: 数据库

---

### SQL FOREIGN KEY 约束

> 一个表中的 FOREIGN KEY 指向另一个表中的 PRIMARY KEY。

-  SQL 在 "Orders" 表创建时为 "Id_P" 列创建 FOREIGN KEY：

###### MySQL

```
create table Orders(
Id_O int NOT NULL,
OrderNo int Not Null,
Id_P int,
primary key(Id_O),
foreign key(Id_P) references Persons(Id_P)
)
```

###### SQL Server / Oracle / MS Access:

```
create table Orders(
Id_O int NOT NULL primary key,
OrderNo int NOT NULL,
Id_P int foreign key references Persons(Id_P)
)
```

- 如果需要命名 FOREIGN KEY 约束，以及为多个列定义 FOREIGN KEY 约束，请使用下面的 SQL 语法

###### MySQL / SQL Server / Oracle / MS Access:

```
create table Orders(
Id_O int NUT NULL,
OrderNo int NOT NULL,
Id_P int ,
primary key(Id_O),
constraint fk_Persons foreign key(Id_P) references Persons(Id_P)
)
```

- 在 "Orders" 表已存在的情况下为 "Id_P" 列创建 FOREIGN KEY 约束，请使用下面的 SQL：

###### MySQL / SQL Server / Oracle / MS Access:

```
alter table Orders
ADD foreign key(Id_P) references Persons(Id_P)
```

- 需要命名 FOREIGN KEY 约束，以及为多个列定义 FOREIGN KEY 约束，请使用下面的 SQL 语法：

###### MySQL / SQL Server / Oracle / MS Access:

```
alter table Orders
ADD contraint fk_Persons(Id_P) references Persons(Id_P)
```

### 撤销 FOREIGN KEY 约束

> 需撤销 FOREIGN KEY 约束，请使用下面的 SQL：

###### MySQL

```
alter table Orders
drop foreign key fk_Persons
```

####### SQL Server / Oracle / MS Access:

```
alter table Orders
drop constraint fk_Persons
```

### SQL CHECK 约束

> CHECK 约束用于限制列中的值的范围。如果对单个列定义 CHECK 约束，那么该列只允许特定的值。如果对一个表定义 CHECK 约束，那么此约束会在特定的列中对值进行限制。

-  在 "Persons" 表创建时为 "Id_P" 列创建 CHECK 约束。CHECK 约束规定 "Id_P" 列必须只包含大于 0 的整数

```

```
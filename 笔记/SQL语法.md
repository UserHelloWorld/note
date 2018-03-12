#SQL语法

|Id|lastName|FirstName|Address|city|
|:-:|:-:|:-:|:-:|:-:|
|1|Adams|John|天安门|北京|
|2|Bush|George|浦东|上海|
|3|Carter|Thomas|龙岗|深圳|


## select语句
```
select 列名称 from 表名称

select * from 表名称 // *代表所有列

```

* 查找一个列

```
select LastName from Person
```

结果为

|LastName|
|:-:|
|Adams|
|Bush|
|Carter|

* 查找多个列

```
select LastName,FirstName from Person
```
结果为:

|LastName|FirstName|
|:-:|:-:|
|Adams|John|
|Bush|George|
|Carter|Thomas|

* 查找所有

```
select * from Person
```

|Id|lastName|FirstName|Address|city|
|:-:|:-:|:-:|:-:|:-:|
|1|Adams|John|天安门|北京|
|2|Bush|George|浦东|上海|
|3|Carter|Thomas|龙岗|深圳|



## distinct
关键词distinct用于返回唯一不同的值

```
select distinct 类名称 from 表名称
```

Order表:

|Company|OrderNumber|
|:-:|:-:|
|IBM|3532|
|W3C|2356|
|Apple|4693|
|W3C|6665|

```
正常查询
select Company from Order
```
结果:


|Company|
|:---|
|IBM|
|W3C|
|Apple|
|W3C|

```
使用关键词distinct
select distinct Company from Order
```

|Company|
|:--|
|IBM|
|W3C|
|Apple|

## where

```
select 列名称 from 表名称 where 列 运算符 值
```

Person表:

|Id|lastName|FirstName|Address|city|Year|
|:-:|:-:|:-:|:-:|:-:|:-:|
|1|Adams|John|天安门|北京|1970|
|2|Bush|George|浦东|上海|1975|
|3|Carter|Thomas|龙岗|深圳|1980|
|4|Gates|Bill|福田|深圳|1985|

```
select * from Person where city = '深圳'
```
结果为:

|Id|lastName|FirstName|Address|city|Year|
|:-:|:-:|:-:|:-:|:-:|:-:|
|3|Carter|Thomas|龙岗|深圳|1980|
|4|Gates|Bill|福田|深圳|1985|

## 引号的使用
 * SQL使用单引号来环绕文本值（大部分数据库系统也接受双引号）。如果是数值（整数，浮点数之类的），请不要用引号（报错）。 

文本值

```
这是正确的
select * from Person where FirstName = 'Bush'
这是错误的
select *from Person where FirstName = Bush
```

数值：

```
这是正确的
select * from Person where Year > 1965
这是错误的
select * from Person where Year > '1965'
```


## and 和 or 运算符

|Id|lastName|FirstName|Address|city|
|:-:|:-:|:-:|:-:|:-:|
|1|Adams|John|天安门|北京|
|2|Bush|George|浦东|上海|
|3|Carter|Thomas|龙岗|深圳|
|4|Carter|William|福田|深圳|

and运算符

```
select * from Person where FirstName = 'Thomas' and LastName = 'Carter'
```
结果为:

|Id|lastName|FirstName|Address|city|
|:-:|:-:|:-:|:-:|:-:|
|3|Carter|Thomas|龙岗|深圳|

or 运算符

```
select * from Person where FirstName = 'Thomas' or LastName = 'Carter'
```

结果为：


|Id|lastName|FirstName|Address|city|
|:-:|:-:|:-:|:-:|:-:|
|3|Carter|Thomas|龙岗|深圳|
|4|Carter|William|福田|深圳|


结合and和or运算符

```
select * from Person where (FirstName = 'Thomas' or FirstName = 'William') and LastName = 'Carter'
```

结果为：

|Id|lastName|FirstName|Address|city|
|:-:|:-:|:-:|:-:|:-:|
|3|Carter|Thomas|龙岗|深圳|
|4|Carter|William|福田|深圳|


## insert into
insert into 语句用于向表格中插入新的行。

语法:

```
insert into 表名称 values (值1,值2,...)
```

我们也可以指定所需要插入数据的列:

```
insert into table_name(列1,列2,...) values(值1,值2,...)
```

Person表:

LastName|FirstName|Address|City|
|:-:|:-:|:-:|:-:|
carter|thomas|龙岗|深圳|

插入新行

```
insert into Person values('gates','bill','福田','深圳')
```

结果:

LastName|FirstName|Address|City|
|:-:|:-:|:-:|:-:|
carter|thomas|龙岗|深圳|
gates|bill|福田|深圳|

在指定列中插入数据

```
insert into Person(LastName,Address) values('wilson','罗湖')
```

LastName|FirstName|Address|City|
|:-:|:-:|:-:|:-:|
carter|thomas|龙岗|深圳|
gates|bill|福田|深圳|
wilson||罗湖||

## Update
update语句用于修改表中的数据

语法:

```
update 表名称 set 列名称 = 新值 where 列名称 = 某值
```

LastName|FirstName|Address|City|
|:-:|:-:|:-:|:-:|
carter|thomas|龙岗|深圳|
gates||福田||

更新某一行中的一个列

```
update Person set FirstName = 'Fred' where LastName = 'gates'
```

结果为：

LastName|FirstName|Address|City|
|:-:|:-:|:-:|:-:|
carter|thomas|龙岗|深圳|
gates|Fred|福田||

更新某一行中的若干列

```
修改地址并添加城市名称
update Person set Address = '罗湖',City = '深圳' where LastName = 'gates'
```

LastName|FirstName|Address|City|
|:-:|:-:|:-:|:-:|
carter|thomas|龙岗|深圳|
gates|Fred|罗湖|深圳|

## Delete
语法

```
delete from 表名称 where 列名称 = 值
```

Person表:

LastName|FirstName|Address|City|
|:-:|:-:|:-:|:-:|
carter|thomas|龙岗|深圳|
gates|Fred|罗湖|深圳|

```
删除某行
delete from Person where LastName = 'gates'
```

LastName|FirstName|Address|City|
|:-:|:-:|:-:|:-:|
carter|thomas|龙岗|深圳|

删除所有行

可以在不删除表的情况下删除所有的行。这意味着表的结构、属性和索引都是完整的

```
delete from table_name
```

或者

```
delete * from table_name
```

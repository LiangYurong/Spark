展示所有数据库

```java
select * from sys.databases
```

查询一张表的字段有多少个

```java
select count(*) from syscolumns where id = object_id('表名')
```

查询一张表中的记录数量

```java
 select count(*)  from 表名
```


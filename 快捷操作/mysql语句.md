展示所有的数据库

```java
SHOW DATABASES;
```

查询一张表的字段有多少个

```java
SELECT count(*) AS fields_count FROM information_schema.COLUMNS WHERE TABLE_SCHEMA = '数据库名' AND table_name = '表名' 
```

 查询一张表中的记录数量

```java
 select count(*)  from 表名
```


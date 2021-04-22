1. show all table spaces

```java
select * from dba_tablespaces;

select name from v$tablespace;

select tablespace_name from user_tablespaces; //use this sql
```

2. show the users of the XXX table space

```java

```

3. check if there is a database named XXX

```java

```

4. show  the path of database file 

```java
select name from v$datafile;
```

5. delete user  named "C##RESEARCH"

```java
drop user C##RESEARCH cascade;
```

6. in cmd . enter "sqlplus" , after login , enter following code to search

```
select * from global_name //GLOBAL_NAME in listener.ora file .

select instance_name from V$instance; // SID_NAME in listener.ora file 
```


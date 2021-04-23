1. show all table spaces

```sql
select * from dba_tablespaces;

select name from v$tablespace;

select tablespace_name from user_tablespaces; //use this sql
```

2. show the users of the XXX table space

```sql

```

3. check if there is a database named XXX

```sql

```

4. show  the path of database file 

```sql
select name from v$datafile;
```

5. delete user  named "C##RESEARCH"

```sql
drop user C##RESEARCH cascade;
```

6. in cmd . enter "sqlplus" , after login , enter following code to search

```sql
select * from global_name //GLOBAL_NAME in listener.ora file .

select instance_name from V$instance; // SID_NAME in listener.ora file 
```

**Query users**

```sql
select user_id,username,default_tablespace from dba_users order by user_id asc;
```

**Query the path of  table space**

```sql
select file_name,tablespace_name from dba_data_files; 
```

**Query all table space**

```sql
select * from v$tablespace;
```

**Query : which users have susdba or sysoper system permissions**

```sql
select * from V$PWFILE_USERS;
```

**check DB version**

```sql
SELECT banner FROM v$version WHERE ROWNUM = 1;
```

**Query user**

```sql
select table_name from user_tables; 
```

**Query table space** 

```sql
SELECT tablespace_name,file_name  FROM dba_data_files;
```

**Query Oracle current container**

```sql
select sys_context('userenv','con_name') from dual;
```

**Query whether a user exists**

```sql
select * from dba_users where USERNAME= 'C##RESEARCH'  ; 
```

**Query whether there are users in a tablespace**

```sql

```


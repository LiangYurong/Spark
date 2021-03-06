
### Basic

用plsql登陆无法使用show指令。

在PL/SQL不能操作的命令，在cmd进入oracle可以进行操作。比如建立表空间，临时表空间，用户等等。

### what is the use of .dmp file

dmp文件导出用的比较多的一般是三种，他们分别是：导出整个数据库实例下的所有数据、导出指定用户的所有表、导出指定表。

### what is the use of CDB



### understand 

用户=商家;表=商品;表空间=仓库

```txt
1. 1个商家能有很多商品，1个商品只能属于一个商家
2. 1个商品可以放到仓库A，也可以放到仓库B，但不能同时放入A和B
3. 仓库不属于任何商家
4. 商家都有一个默认的仓库，如果不指定具体仓库，商品则放到默认的仓库中
```
### table space , user , table

1. oracle中用户的所有数据都是存放在表空间中的，很多个用户可以共用一个表空间，也可以指定一个用户只用某一个表空间。
2. 表空间：创建表空间会在物理磁盘上建立一个数据文件，作为数据库对象（用户、表、存储过程等等）的物理存储空间；
3. 用户：创建用户必须为其指定表空间，如果没有显性指定默认表空间，则指定为users表空间；创建用户后，可以在用户上，创建表、存储过程等等其他数据库对象；
4. 表：是数据记录的集合；
```txt
创建过程： 表空间--->用户--->表;
所属关系： 表空间 包含 用户 包含 表；
```

### ORACLE的整体结构。

oracle中的一个数据库就是一个实例.

oracle的一个用户就是一个Schema（即方案）.
oracle的结构是:实例->用户->表（用户属于数据库实例,表属于某个用户）

所以在oracle下建立 建表空间，建用户，设置用户的默认表空间，在用户下建表；

### 查看用户与切换用户

1. 打开运行界面，输入cmd命令
2. 在命令行输入sqlplus命令
3. 输入用户名和密码进入sqlplus环境
4. 执行show user命令显示当前用户
5. 输入conn 用户名/密码 命令进行用户切换
6. 输入show user命令查看用户是否切换

### 注意点

1. 对于Oracle，创建完数据库后，并不能立即在数据库中建表，必须先创建该数据库的用户，并且为该用户指定表空间。
2. 当我们要使用Oracle作为项目的数据库时，我们需要先创建数据库实例（如orcl），之后创建表空间，再创建相对应的表（也就是逻辑结构中的数据段）

案例1、根据表空间创建语法，创建一个100M大小数据文件（student.dbf）的表空间student，代码如下：
```text
create tablespace student
datafile 'E:\APP\ADMIN\ORADATA\ORCL\student.DBF'
size 100m
autoextend on next 10m maxsize 500m
permanent
extent management local;
```
案例解析：
创建一个student表空间，指定了数据文件为“E:\APP\ADMIN\ORADATA\ORCL\student.DBF”，表空间是自动扩展的，每次自动扩展大小为10M，最大扩展到500M，创建的是永久表空间，用来存储student用户的数据库对象和数据，管理模式为本地管理。


### 临时表

临时表就是用来暂时保存临时数据（亦或叫中间数据）的一个数据库对象，它和普通表有些类似，然而又有很大区别。它只能存储在临时表空间，而非用户的表空间。ORACLE临时表是会话或事务级别的，只对当前会话或事务可见。每个会话只能查看和修改自己的数据。

1. oracle创建表空间
2. 创建用户
3. 用户授权

### oracle新建数据库

1、创建数据库实例一般使用“配置移植工具 -> Database Configuration Assistant”来创建。

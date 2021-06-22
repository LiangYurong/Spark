
### 导出数据库表和数据

1. 登录PL/SQL Developer
2. 菜单栏选择 - 工具 - 导出表
3. 选择用户
4. 选择SQL插入，勾选创建表，选择存放文件路径和文件名称，然后用鼠标左键拖动选择表，点“导出”即可。

打开工具，新建一个sql窗口，按F8执行，
```text
create  tablespace db_test --表空间名
datafile 'D:\lyr\oracledata\20210204\test.dbf' --物理文件 表空间数据文件存放路径
size 50m  --大小初始值
autoextend on  --自动扩展
next 50m maxsize 20480m  --每次扩展50m，最大为20480m
extent management local;
```

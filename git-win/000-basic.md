### basic

if you fail to push in IDEA , try to use command line .

if you fail to push in command line , try to use IDEA.

### basic command

查看当前git管理的代码状态：git status。红色显示的文件代表：还没被添加到库里，还不受库的管理和跟踪。

把当前未提交的内容全部还原，也就是删除之前的一些操作：git checkout . （慎重使用）

查看分支：git branch    

如果有main和master两个分支，当前是master分支，切换到main分支的命令：git checkout main

## 安装与配置git

#### 安装与配置

1、安装git

2、配置用户名：git config --global user.name "xxx"

3、配置邮箱：git config --global user.email "xxx@qq.com"

####  配置密钥（一台机器只需要配置一次）

1、创建密钥，打开git cmd，输入命令，一路回车：ssh-keygen -t rsa -C "794842744@qq.com"

2、生成的密钥文件在C:\Users\Administrator/.ssh文件夹中的id_rsa.pub。用notepad++打开，全部复制

3、在github设置的setting添加一个密钥。

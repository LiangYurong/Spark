### 补充

第一次本地push到空的仓库：git push -u origin --all

### 1、本地连接git步骤（只需操作一次即可）

- 下载并安装git。 

- 新建一个文件夹，任意起名。右键选择git bash。

- 输入：git init

- 输入：git config --global user.name "你的名字" （我的是liangyurong）

- 输入：git config --global user.email "你的邮箱"（ 我的是794842744@qq.com）

- 本地电脑使用Listary软件全局搜id_rsa.pub，复制里面所有内容，去到gitlab。新增SSH keys，直接粘贴到key框，会自动生成title。点击保存即可。

### 2、如果ssh显示无效或者链接失败

- 删除与id_rsa.pub同层级的文件known_host。

- 然后去到ssh文件夹，右键选择bash here。执行 ssh-keygen -t rsa -C  '794842744@qqcom'  重新生成ssh。输入之后一直enter即可。

- 之后再去gitlab重新设置ssh。

### 3、拉取项目的master到本地

- 需要对应ip，如果是localhost显示的，需要看地址栏显示的是什么地址。

- 比如http://localhost:8888/lyr/hello.git是不对的。然后地址栏显示的是http://main.yurong333.com:8888/lyr/hello。因此需要更改为http://main.yurong333.com:8888/lyr/hello.git

- 正确代码：git clone http://main.yurong333.com:8888/lyr/hello.git

### 4、拉取gitlab项目的分支项目到本地

- 在gitlab中新建一个分支，取名为lyr。

- 在本地电脑，新建一个文件夹，命名为test。

- 在test文件夹里，右键选择git bash here。

- 输入：git init

- 输入：git remote add origin http://main.yurong333.com:8888/lyr/hello.git

- 拉取远程指定分支：git fetch origin lyr

- 新建本地分支并关联到指定远程分支：git checkout -b lyr origin/lyr

- 执行完上述代码，会拉取gitlab的代码到本地分支。

### 5、将本地项目push到gitlab分支

- 首先进行操作：**拉取gitlab分支项目到本地，然后再更新项目，最后再push最好**。

- 拉取分支项目到本地后，然后更新文件，之后再输入下面的代码

- 输入：git add .

- 输入：git commit -m "写上你需要补充的信息"

- 连接到远程仓库：git remote add origin http://main.yurong333.com:8888/lyr/hello.git

- push到远程分支，lyr是分支名称：git push -u origin lyr

### 6、本地项目提交到master进行更新

需求：本地项目已经更新了代码，但是gitlab的master还没更新代码，因此需要本地提交来更新gitlab的master的代码。

```java
git add .

git commit -m '写上你的提交信息'

git push -u origin

```
### 7、gitlab的master更新了项目，我本地的项目和master的不一样，现在需要将master的拉取下来合并到我的本地项目

```java
//查询当前远程的版本
$ git remote -v

//获取最新代码到本地(本地当前分支为[branch]，获取的远端的分支为[origin/branch])
$ git fetch origin master  [示例1：获取远端的origin/master分支]
$ git fetch origin dev [示例2：获取远端的origin/dev分支]

//查看版本差异
$ git log -p master..origin/master [示例1：查看本地master与远端origin/master的版本差异]
$ git log -p dev..origin/dev   [示例2：查看本地dev与远端origin/dev的版本差异]

//合并最新代码到本地分支
$ git merge origin/master  [示例1：合并远端分支origin/master到当前分支]
$ git merge origin/dev [示例2：合并远端分支origin/dev到当前分支]
```
如果出现提示信息
```java
Please enter a commit message to explain why this merge is necessary, especially if it merges an updated upstream into a topic branch
```
则采取的操作是
```java
1. press "i" (i for insert)

2. write your merge message

3. press "esc" (escape)

4. write ":wq" (write & quit)

5. then press enter
```
### 8、将本地的代码合并到gitlab的master

一、在dev分支上运行以下命令

```java
　　1. git add . // 暂存所有更改

　　2. git commit -m "更改的备注信息" // 将修改 提交到本地仓库，双引号内是提交的备注信息

　　3. git pull origin lyr // 拉取远程lyr分支代码

　　4. git push origin lyr // 将本地修改的代码提交到远程的lyr分支上

　　5. git checkout master // 切换到master分支
```

二、在master分支上运行以下命令

```java
　　1. git merge lyr// 将lyr分支的代码合并到master上

　 2. git push origin master // 将当前的更改推送到远程的master分支上
```

执行完以上命令，此时lyr分支与master分支的代码已同步。

三、可能用到的命令

```java
　　1.  git checkout  // 可以看到当前的所处的分支位置，位于master还是dev等。
　　2.  git log  // 可以看到近期的相关提交日志（提交时候的备注等）
　　3.  git status  // 可以看到当前的文件状态 （如xx文件被修改，但未提交等）
```


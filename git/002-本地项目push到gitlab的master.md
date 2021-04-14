### 需求

在本地已有项目，gitlab没有的情况下，如何把本地新项目推送到远程仓库上

### 本地操作

1. 去到项目的主路径，右键点击“git bash here”

```java
git init  //初始化本地仓库

git add .   //将本地项目的所有文件添加到暂存区

git commit -m "说明信息"
```

### 终端

1. 首先，建立本地仓库和远端GitLab仓库的关联关系。

```java
git remote add origin  https://gitlab*********************.git

在这一步时如果出现错误：fatal:remote origin already exists，先清除一下关联关系在进行上一步动作：git remote rm origin

```

2. 检查关联是否已建立且正确：

```java
git remote -v
```
3. 推送到gitlab的master
```java
git push -u origin master
```

4. 至此，操作成功。

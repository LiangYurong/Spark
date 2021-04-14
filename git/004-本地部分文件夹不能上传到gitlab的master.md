### 1、需求与背景

本地需要将一个前端项目push到gitlab的master。gitlab只是新建了project但是没有代码。

### 2、没有提交的文件夹

docker文件夹

node文件夹

### 3、没有push的原因

查看.gitignore文件，发现这两个文件的目录名在里面，因此没有上传这两个文件夹。

### 4、解决问题的步骤

在本地项目目录，打开.gitignore文件，删除里面的两个目录名称。重新push一遍。

```java

git add . 

git commit -m '上传docker和node文件夹'

git push -u origin

```

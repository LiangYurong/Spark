### 一、需求

本地文件夹为空，需要将gitlab的项目clone到本地文件夹。

### 二、操作

1. 新建test文件夹。

2. 进入文件夹，右键选择git base here,输入下面的代码。

```java

git init

git config --global user.name "liangyurong"  //对应gitlab上面你的名称

git config --global user.email "liangyurong@qq.com"  //对应gitlab上面你的email

git clone http://main.sdyunban.com:8888/liangyurong/gdydops.git  // 需要对应仓库的http连接
 
```

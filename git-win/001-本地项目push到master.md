### 一、project background

push local project to empty repository on gitlab website 

### 二、local operation

1. **first  link** : open project folder  , right click to select  "git bash here"

```java
git init  

git config --global user.name "your name" 
// git config --global user.name "liangyurong" 
    
git config --global user.email "your email"
// git config --global user.email "liangyurong@qq.com" 

git remote add origin  https://gitlab*********************.git       
// git remote add origin http://120.78.12.228:8888/liangyurong/OrderWeChatPay.git

git add .   

git commit -m "commit message" 

git push -u origin master
```

2. 之后只需要这么做

```
git add .   

git commit -m "commit message" 

git push -u origin master
```

### 如果之前给的git项目地址是错的，然后现在输入新的地址，结果出错。现在需要设置新的项目地址。

```txt
error: remote origin already exists.
```

operation
```txt
git remote rm origin
git remote add origin  https://gitlab*********************.git       
```

### pull the master of the project to local

- not recommend

```
git init

git config --global user.name "liangyurong"  //replace with your name
// git config --global user.name "794842744"

git config --global user.email "liangyurong@qq.com"  //replace with your email
// git config --global user.email "794842744@qq.com"

git remote add origin http://main.yurong333.com:8888/liangyurong/test.git //replace with your http link of repository
// git remote add origin https://github.com/liangyurong/bug-bug-bug.git

git clone http://main.yurong333.com:8888/lyr/hello.git
// git clone https://github.com/liangyurong/bug-bug-bug.git

```

- recommend

```
git init

git config --global user.name "liangyurong"  //replace with your name

git config --global user.email "liangyurong@qq.com"  //replace with your email

git remote add origin http://main.yurong333.com:8888/liangyurong/test.git //replace with your http link of repository

git pull --rebase origin master
```

### points to note

- if the address bar shows localhost ,

```
wrong:    http://localhost:8888/lyr/hello.git

right:    http://main.yurong333.com:8888/lyr/hello.git
```


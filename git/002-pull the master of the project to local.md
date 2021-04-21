### pull the master of the project to local

- not recommend

```
git init

git config --global user.name "liangyurong"  //replace with your name

git config --global user.email "liangyurong@qq.com"  //replace with your email

git remote add origin http://main.yurong333.com:8888/liangyurong/test.git //replace with your http link of repository

git clone http://main.yurong333.com:8888/lyr/hello.git
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


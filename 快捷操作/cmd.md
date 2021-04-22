查看某个端口的占用情况

```
netstat -aon|findstr "8081"
```

杀掉占用端口的进程（比如占用8081端口的是2000）

```
taskkill /f /pid 2000
```

打开本地服务

```
services.msc
```

open 

```
regegit
```

ping某个ip地址

```
ping 127.0.0.1
```

show  local hostname

```
hostname
```


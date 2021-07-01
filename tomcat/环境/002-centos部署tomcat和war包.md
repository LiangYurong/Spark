


### 一、下载tomcat8.5.68

link：https://tomcat.apache.org/download-80.cgi

选择core下面的tar.gz(pgp,sha512)。

tomcat压缩包文件名称：apache-tomcat-8.5.68.tar.gz

### 二、安装tomcat

登录winSCP，将压缩包放到文件夹：/usr/local/tomcat

从XSHELL中登录，进入文件夹：cd /usr/local/tomcat

解压：tar zxvf apache-tomcat-8.5.68.tar.gz

删除压缩包：rm -f apache-tomcat-8.5.68.tar.gz

重命名文件夹apache-tomcat-8.5.68为tomcat_wechatorderpay_8078：mv  apache-tomcat-8.5.68  tomcat_wechatorderpay_8078

### 三、部署war包

```text
cd tomcat_wechatorderpay_8078

cd webapps

删除掉除ROOT文件夹外的所有文件夹
rm -rf  docs
rm -rf examples
rm -rf host-manager
rm -rf manager

将war包放进webapps文件夹

```

### 启动与关闭

首先需要进入到bin文件夹

启动tomcat：./startup.sh

关闭tomcat：./shutdown.sh

使用./startup.sh启动tomcat之后，再使用./shutdown.sh关闭tomcat
1. 去到webapps文件夹。
2. 删除ROOT文件夹里的所有文件。
3. 下面会生成一个tomcat_wechatorderpay_8078文件夹，将tomcat_wechatorderpay_8078文件夹里的全部文件移动到webapps文件夹下的ROOT文件夹。

### 虽然tomcat_wechatorderpay_8078里的工程访问端口是8078，但是浏览器那边的访问端口还是8080

比如访问：http://134.175.207.83:8080/hi，成功

比如访问：http://134.175.207.83:8078/hi，失败

因此需要更改tomcat的访问端口
- 进入conf目录，修改server.xml，输入命令：vi server.xml 
- 进入之后，输入i，可以编辑。
- 编辑完，按Esc退出编辑
- 编辑完，保存并推出    :wq
- 编辑完，不保存就推出  :q!

修改的端口在这，将8080改为你的端口
```text
<Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />

```
















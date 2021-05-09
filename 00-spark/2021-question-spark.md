



## 2021-05

### 001-东鹏特饮的那个透明盖子是拿来做什么的？

链接：https://www.zhihu.com/question/39324406
- 防尘
- 产品标识
- 防伪
- 分享
- 
## 2021-04

### 017-Xshell可以做什么？

### 016-powershell这么牛逼吗？除了命令行，还可以做什么？

### 015-什么是软路由？

### 014-frp又是什么？可以搞内网穿透？

### 013-内网穿透是什么？可以做什么？

### 012-为什么电脑需要端口？端口是做什么的？

### 011-磁力链接是怎么形成的？如果我上传一部电影，怎么生成磁力链接？

### 010-对自己的github仓库进行全局搜索？

### 009-适合程序员的搜索引擎，或者搜索工具？

1. https://stackoverflow.com/
2. https://goobe.io/
2. https://kaifa.baidu.com/
3. http://www.blogsearchengine.org/
4. https://superuser.com/questions/120045/how-to-execute-sh-file-on-windows

### 008-你发现了什么宝藏up？博主？有趣的博客？干货满满的博客？



### 007-用什么替代印象笔记？

我对笔记的要求：目录分类，全局搜索，版本控制，markdown编写。

IntellIJ + git + github + Typora

IntellIJ:多目录，全局搜索，编写md，版本管理。

### 006-使用中文搜索，能不能展示中英文搜索结果

暂时没想到什么脚本或者插件。

### 005-github怎么使用图片链接？

1. 首先建立一个仓库，起名为imageHouse，作为外链链接。

2. 上传图片到该仓库。只能一次一个。或者你可以在本地push到仓库。

3. github上其他需要使用到图片的地方，就打开图片，右键，复制图片地址，粘贴到相应的地方，引用成功。

### 004-怎么屏蔽csdn左侧栏？

greasy插件安装一个脚本即可。[链接](https://greasyfork.org/zh-CN/scripts/378351-%E6%8C%81%E7%BB%AD%E6%9B%B4%E6%96%B0-csdn%E5%B9%BF%E5%91%8A%E5%AE%8C%E5%85%A8%E8%BF%87%E6%BB%A4-%E4%BA%BA%E6%80%A7%E5%8C%96%E8%84%9A%E6%9C%AC%E4%BC%98%E5%8C%96-%E4%B8%8D%E7%94%A8%E5%86%8D%E7%99%BB%E5%BD%95%E4%BA%86-%E8%AE%A9%E4%BD%A0%E4%BD%93%E9%AA%8C%E4%BB%A4%E4%BA%BA%E6%83%8A%E5%96%9C%E7%9A%84%E5%B4%AD%E6%96%B0csdn/code)

顺便安装“网页宽屏”脚本。

### 003-浏览知乎话题下面的回答，右边栏总是有其他话题，能不能屏蔽，变成一个纯净版的页面？

油猴脚本安装知乎美化脚本：[知乎美化脚本链接](https://greasyfork.org/zh-CN/scripts/402808-%E7%9F%A5%E4%B9%8E%E7%BE%8E%E5%8C%96)

安装之后，整个世界都清净了。

### 002-人是不是应该学点理财知识？

比如学基金知识。可以去公众号看下介绍。

### 001-怎么快速生成一个maven项目？

总是要按部就班得创建maven项目，然后导入SpringBoot依赖，再创建主运行类，是真的很烦。应该怎么做呢？


## 2021-03

#### 013 - MAC变服务器

#### 012 - 怎么写epub

typora安装pandoc之后可以导出epub。

#### 011 - 怎么像看母语一样看中文？

#### 010 - 在实体类的字段上注释不好看，怎么办？

采用swagger的@ApiModelProperty注解
```java
@ApiModelProperty(value = "问题类型的编码",example = "0")
@Column
private Integer quTypeCode;
```
#### 009-WEBDAV服务是什么？

webdav就像一个存储服务，各种应用都可以连接到它，允许应用直接访问我们的云盘内容，对其进行读写操作。我们可以网络服务比作一只章鱼，云盘是它的大脑，WebDAV是它的触角。每个触角都连接到我们智能设备上的应用程序。我们的应用可以通过触角读取章鱼的大脑，并将数据写入大脑，改变大脑的记忆和内容。

有哪些支持webdav的网盘？
国外网盘：Box、Dropbox、teracloud、yandex、TransIP
国内网盘：坚果云、城通网盘
私有云：OwnCloud、Seafile 、群晖
目前国内最好用的支持webdav：坚果云

#### 008-自建笔记系统，历史版本管理，笔记如何分类。笔记如何备份。比如定期备份到onedrive中。然后清除半年前的备份。markdown编写。

### 007 - 坚果云的全局搜索

好像付费用户可以使用全局搜索，但是不知道能不能搜索到文件内容。

免费用户没有文件全局搜索功能，付费用户才有

#### 006 - 有些网站比较慢，就会提供镜像网站。原理是什么？

#### 005-java调用python的算法吗？

执行python脚本文件

#### 004-印象笔记设置代码块字体默认大小？

2021/3/3，已经有人在豆瓣上提出了这个需求，印象笔记官方也回复了，结果现在都没实现。

ctrl + 组合按键，可以变大。

#### 003-  rJava是一个R语言和Java语言的通信接口，通过底层JNI实现调用，允许在R中直接调用Java的对象和方法。
（原来其他的东西还是可以和java互通的）

#### 002-带括号的加减乘除是怎么实现的，用什么数据结构实现？（栈，后缀表达式）


#### 001 - 程序员有孩子之后，还有多少时间学习提高？

2021/03/01。一个大学同学今天生了儿子。真的是人生无限奇妙啊。我感觉，当我结婚有孩子之后，我就几乎没什么时间了、所以趁现在能学习就赶紧学习，不要再去看什么垃圾节目，赶紧学习，娱乐的东西可以集中一段时间再看


## 2021-02

#### 012-付费使用Netflix播放器需要科学上网。

#### 011 - 台式电脑处于关机的状态是否可以自动开机？
BIOS设置自动开机和小米智能插座。

#### 010 - 显示屏和笔记本桌面的软件排列是否能设置一样？

#### 009 - 有没有哪个笔记软件，能记录内容的被使用频次，进行笔记实际利用率的分析，便于整理（整理自v2ex）
比如说今天要编译个 nginx，然后从知识库里找到了对应的内容块。系统能够对这个内容块++1，后面就进行统计，就可以分析知识库内笔记的利用率。。。能定位出哪些内容经常被使用，哪些是记到笔记里后，从来没派上用场的。

#### 008 - Intel Nuc有什么用？和nas差不多吗？

#### 007 - 把内存划给RAM盘是什么操作？

#### 006 - 使用遗传算法训练其他算法？比如用遗传算法训练解数独算法？

### 005 - 一个GitHub仓库只放一个项目吗？如果仓库达到上百个，该怎么处理？

#### 004 - 印象笔记几千条，怎么整理？你是用什么方法的？ 

#### 003 - 怎么最大化发挥印象笔记的效果？你是怎么用的？

#### 002 - 通过Apache http服务共享，这个可以做什么？

#### 001 - java编程中能够少用鼠标吗？

2021/03/25，目前来说，要用到鼠标的地方还是非常多的。


## 2021-01

#### 001 - 有没有个人博客的搜索引擎？
小蛇搜搜：https://xiaoshesoso.com/。体验一般。

目前使用的搜索方法google+englishsite:xxx.com keyword
搜索自己订阅的rss进行搜索

#### 002 - 能不能只在自己的rss列表搜索东西？

#### 003 - 树莓派能够做什么？

#### 004 - 程序员喜欢鼓捣什么软件和硬件？

#### 005 - 工作站是什么？怎么鼓捣一个工作站？

#### 006 - 听歌识曲怎么实现的？

#### 007 - 台式机外接mac屏幕？

#### 008 - chrome标签页怎么显示多行？

#### 009 - 一个tomcat能够同时启动两个SpringBoot项目吗？

#### 010 - windows端写个脚本定时将本地项目push到github？

写个.bat，windows打开“任务计划程序”，设置好触发器，每隔一个钟上传到github，美滋滋。

#### 011 - 国外有什么好的技术网站？特别是java的技术网站？

#### 012 - 手机能跑linux吗？

#### 013 - 旧笔记本显示屏如何弄成单独的显示屏？

#### 014 - 英文软件可以考虑使用汉化版本。IDEA汉化变卡吗？

#### 015 - 旧笔记本有什么用搞软路由。
内网穿透做远程开发环境？
旧手机，旧电脑都刷linux，拿来组本地集群。行得通吗？
装ubuntu可以做什么？跑 Linux 。
把一些基本固定不动的微服务，比如网关和认证之类的，还有数据库之类玩意的扔上去跑。性能还有剩的可以当下载机和媒体服务器。还可以跑一些耗时的东西，比如跑 waifu2x 处理图片什么的。可以当服务器，跑些 docker, nas。
#### 016 - .bat能够执行sh脚本吗？可以。

#### 017 - 怎么设定执行.bat脚本的默认浏览器是chrome，而不是其他浏览器？
windows - 设置 - 主页 - 默认应用 - web浏览器 - 选择chrome

#### 018 - 还有哪些东西可以折腾的呢？比如nas，树莓派，旧笔记本，穷装机。

#### 019 - github能不能调节字体颜色？

不能。但是可以内嵌HTML。

#### 020 - 有直接是linux系统的笔记本吗？
好像是没有。笔记本装个VM就可以了吧。

#### 021 - 个人博客项目可以放到github运行吗？怎么支持快速全局搜索？
用ES？

#### 023 - .bat文件使用chrome打开网站
start chrome "google.com"
start chrome "cnblogs.com"
start chrome "v2ex.com"
start chrome "tophub.today"

## 印象笔记星火

#### 005-怎么使得全局搜索快速搜索到自己想要的笔记？

做笔记，在开头可以写：几个自己能够立即想到的关键词，以后大概率能快速搜索到需要的笔记。

#### 004-印象笔记代码块的字体大小不能调整

暂时不可以，但是通过ctrl和+的组合操作可以放大字体。

#### 003-可不可以看自己每个月新增了多少条笔记？

#### 002-想法产生很快，消失也很快

有时候记不住笔记标题或者内容里面的关键词的时候，很难通过搜索来找到以前的笔记。

偶尔复习笔记的时候发现，我在不同的时候写过内容几乎一样的笔记；发现对以前记得笔记的重复利用很少。

我碎片化的新想法比较多，但是新想法冒出来的时候，脑海里的印象还比较浅，如果不能立刻记下来，可能十几秒后就忘记了，然后要再回忆起来就难了。

2021/2/8。目前我也是遭遇了这个问题，我现在的笔记已经有1k多了，也会找不到自己想要的笔记

#### 001-使用印象笔记客户端（中国）卡顿

工单描述
```java
当前版本 ：clash for window，印象笔记客户端（中国）
问题描述 ：打开clash之后，使用印象笔记会出现卡顿现象。关闭clash之后卡顿消失。
求助 ：是否可以设置印象笔记客户端不走clash的流量？如何设置？或者有其他解决方法？
```
解决方法
```java
1、打开clash客户端，关闭"system porxy"
2、chrome安装插件“Procy SwitchyOmega”即可，设置哪些走代理哪些走直接流量
```



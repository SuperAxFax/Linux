# Linux

## 1：Linux内容介绍

(1)：为什么要在这个时间点学习Linux? Java全栈开发的我们需要掌握哪些知识？需要准备什么样的工作？

Java开发之路： 

- JavaSE, MySQL, 前端(HTML,CSS,JS), JAVAWeb, SSM框架, SpringBoot, Vue ,SpringCloud, (MP Git)

- Linux(Centos7)是个操作系统。Linux的一切皆文件，就是读写。

- 消息队列(Kafka, RabbitMQ, RockeetMQ), 缓存(Redis), 搜索引擎(ES)

- 集群分布式(需要购买多台服务器，如果没有服务器我们使用虚拟机也可以)

学习方式：
1：认识Linux

2：基本的命令(重点: Git讲了一些基本的命令(文件操作，目录管理，文件属性，Vim编辑器, 账号管理，磁盘管理,,,,,,))

3：软件安装和部署！(java, tomcat, docker)

4：学习顺序Linux-->Redis-->Docker

## 2：Linux入门概述

### 1：我们为什么要学习Linux

​        习惯使用windows操作系统，再让大家切换到别的操作系统基本上是不可能的事情，改变一个人已经养成的习惯很难。没有办法深入到普通老百姓的生活，这并不意味着Linux没有用武之地。在服务器端，在开发领域Linux则是越来越受到欢迎，很多程序员都觉得不懂点Linux都觉得不好意思，Linux在开源社区的地位依然是岿然不动。尤其是作为一个后端程序员，，是必须要掌握Linux的，因为这是找工作的基础门槛。

### 2：Linux简介

- Linux内核最初由芬兰人林纳斯.托瓦兹上大学时处于个人兴趣编写。

- Linux是一套免费使用和自由传播的类Unix操作系统，是一个基于POSIX(可移植操作系统接口)和Unix的多用户，多任务，支持多线程和多CPU的操作系统。
- Linux能运行主要的Unix工具软件，应用程序和网络协议。它支持32位和64位硬件。Linux继承了Unix以网络为核心的设计思想1，是一个性能稳定的多用户网络操作系统。

### 3：Linux发行版

Linux发行版简单点说就是将Linux内核与应用软件做一个打包。

下图为Linux的版本：

![1651491508495](Linux.assets/1651491508495.png)

目前市面上比较知名的发型版本有：Ubuntu, RedHat，CentOS，Debian，SuSE，OpenSUSE，Arch Linux，SolusOS等。

![1651491553864](Linux.assets/1651491553864.png)

### 4：Linux应用领域

​     今天各种场合都有使用各种Linux发行版，从嵌入式设备到超级计算机，并且在服务器领域确定了地位，通常服务器使用LAMP(Linux + Apache + MySQL + PHP)或LNMP(Linux + Nginx+ MySQL +PHP)组合。

​     目前Linux不仅在家庭与企业中使用，并且在政府中也很受欢迎。



## 3：阿里云上的一些知识：

1：所要开启的安全组中一些端口号的含义：

![1651492910762](Linux.assets/1651492910762.png)

2：开启一个新的端口号的方法：

![](Linux.assets/1651493047714.png)



## 4：使用xshell连接本地虚拟机上的centos7

步骤：

1：确认虚拟机拥有openssh-server服务：
输入： which ssh

显示：/user/bin/ssh说明存在该服务

2：安装xshell软件

3：进行设置

(1)：输入: ifconfig来获取虚拟机的ip地址

(2)：使用xshell进行连接并进行设置。必须设置的有主机名称，地址，密码。

4：另外一种连接的方法

在cmd输入：ssh root@192.168.179.128进行连接。

```java
步骤：
  1：which ssh
  2：ifconfig
  3：xshell中新建连接
```

补充：在使用xshell连接时跳出的一张图：

![1651497069668](Linux.assets/1651497069668.png)

## 5：使用xftp将文件上传到虚拟机上的centos7

![1651498726736](Linux.assets/1651498726736.png)

```java
Linux中的命令：
  1:进入中文文件：cd ~/桌面/
  2:删除某个文件：rm -rf 文件名
  3:显示文件下的内容：ls   
  4:以行的形式显示文件下的内容：ls -ll
  5:最全的显示为,表示查看全部文件：ls -al
```

## 6：开机关机和基本目录介绍

### 1：开关机

![1651500343499](Linux.assets/1651500343499.png)

```java
开关机的Linux命令：
     1：将数据从内存同步到硬盘：sync
     2：立即关机指令：shutdown -h now
     3：重启：reboot
```

### 2：系统目录结构

(1)：一切皆文件

(2)：根目录/ ，所有的文件都挂载在这个节点下

![1651501167011](Linux.assets/1651501167011.png)

- /bin：bin是Binary的缩写，这个目录存放着最经常使用的命令。
- /boot：这里存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件。(不要动)
- /dev与/mnt：dev是Device的缩写，存放的是Linux的外部设备，在Linux中访问设备的方式和访问文件的方式是相同的。  /mnt是系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在/mnt上，然后进入该目录就可以查看光驱里的内容了。(我们后面会把一些本地文件挂载在/mnt目录下)
- <span style="background:#FF9999;">/etc：这个目录用来存放所有的系统管理所需的配置文件和子目录。</span>后面的java,redis等这些配置都放在这里面。
- /home：用户的主目录，在Linux中，每个用户都有一个自己的目录，一般该目录是以用户的账号命名的。
- /lib：这个目录里存放着系统最基本的动态连接共享库，其作用类似于Windows里的DLL文件。(不要动)
- /media：Linux系统会自动识别一些设备，例如U盘，光驱等。当识别之后，Linux会把识别的设备挂载到这个目录下。
- <span style="background:#FF9999;">/opt：这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库则可以放在这个目录下。默认是空的。</span>
- <span style="background:#FF9999;">/root：该目录为系统管理员，也称作超级权限者的用户主目录。</span>
- /tmp：存放一些临时文件
- <span style="background:#FF9999;">/user：这是一个非常重要的目录，用户的很多应用程序和文件都放在则个目录下，类似于windows下的program files目录。</span>

```java
创建文件夹的Linux命令
  1：在某个目录下创建文件夹：mkdir 文件夹名
  2：将文件移动到指定的文件夹：mv 文件名 文件夹名
  3：进入系统文件夹与自己创建的文件夹的区别：自己创建的直接 cd  fax，不需要要加/
  
```

## 7：目录相关命令学习

```java
1:ls :列出目录
    ls -a : all,查看全部文件
    ls -l : 列出所有文件的权限和属性，没有隐藏文件
  所有的Linux命令可以组合使用。
2:cd :切换目录(绝对路径都是以/开头，相对路径是../开头)
    cd /home :进入当前文件夹下的文件夹
    cd ../usr :相对路径进入usr目录
    cd /home/superax: 绝对路径跳转
    cd ..: 返回上一层目录下
    cd: 直接返回根目录
3:pwd :显示当前用户所在的目录

4:mkdir: 创建目录
    mkdir fax: 创建一个目录
    mkdir -p test2/test2_2: 创建多级目录
5:rmdir: 删除目录(rmdir只能删除空的目录。如果下面存在文件，需要先删除文件，删除多级目录要用-p)
    rmdir test1: 删除一个目录
    rmdir -p test2/test2_2: 删除多级目录
6:cp:(复制文件或者目录)
    cp 原来的地方 新的地方 （如果新的地方有相同的文件，输入y进行覆盖即可）
7:rm(移除文件或者目录)
   rm -f: 强制删除
   rm -r: 递归删除目录
   rm -i: 互动，询问是否删除
   删库跑路: rm -rf
8:mv:移动文件或者目录
   mv 原来位置 现在位置（移动文件）
   mv 原来的文件名 新的文件名（重命名文件）
   mv -f:强制移动
   mv -u:只替换已经更新过的文件
```

##    8:  文件属性查看及其修改

![1651577713701](Linux.assets/1651577713701.png)

1：Linux中第一个字符表示这个文件是目录，文件，或者链接文件等等。

- 当为[d]表示目录
- 当为[-] 则是文件
- 若是[I]表示为链接文档(link file)

2：接下来的字符中，以三个为一组，且均为[rwx]三个参数的组合。其中,[r]代表可读，[w]代表可写，[x]代表可执行。这三个权限的位置不会变，如果没有权限就使用-表示。

![1651578182038](Linux.assets/1651578182038.png)

3：修改文件属性的方法

各个权限的数字为： r:4  w:2  x:1

chmod 777 www: 表示的是将www的权限设为rwxrwxrwx

chmod 700 superax: 表示的是将superax的权限设为rwx------

## 9:  文件查看

网络配置目录：cd  /etc/sysconfig/network-scripts

```java
1: cat 由第一行开始显示文件内容，用来读文章，或者读取配置文件（cat ifcfg-ens33）
2: tac 由最后一行开始显示，可以看出tac顺序正好与cat相反（tac ifcfg-ens33）
3: nl 显示的时候前面会包含行号，相当于加行号的cat（nl ifcfg-ens33）
4: more 表示一页一页的显示文件内容（空格表示翻页，enter表示向下看一行）（more csh.login）
5: head与tail  head看头几行，tail看末尾几行。（head -n 20 csh.login表示看前20行）
```

## 10：软链接与硬链接

Linux的链接分为两种，软链接和硬链接

硬链接：A---B，假设B是A的硬链接，那么它们两个指向同一个文件！允许一个文件拥有多个路径，用户可以通过这种机制建立硬链接到一些重要文件上，防止误删！

软链接：类似于Window下的快捷方式，删除了源文件，快捷方式也访问不了！

```java
//补充的两个Linux命令
  1: touch f1 创建文件
  2: echo "i love fax" >>f1（在f1文件中写入:i love fax）
  2: ln f1 f2 创建硬链接f2（f1事先已经存在）
  3: ln -s f1 f3 创建软链接f3（f1事先已存在）
```

结果：在删除f1源文件之后，硬链接f2中仍存在i love fax,但是软链接创建的f3已经没了任何内容。

## 11：Vim编辑器的使用

1：Vim具有查看内容，编辑内容，保存内容的功能。

2：Vim的三种使用模式：分别是命令模式(Command mode), 输入模式(Insert mode)和底线命令模式(Last line mode)。这三种模式作用分别是：

- 命令模式：用户刚刚启动vim就进入了命令模式
- 此状态下敲击键盘动作会被

>工作计划：最重要的是Linux急不得。不要着急，先完成老师安排的任务之后，再继续学习，不要过分焦躁即可。来了蟹不肉。

## 11：Vim编辑器的使用

1：Vim具有查看内容，编辑内容，保存内容的功能。

2：Vim的三种使用模式：分别是命令模式(Command mode), 输入模式(Insert mode)和底线命令模式(Last line mode)。这三种模式作用分别是：

用户刚进来就进入命令模式--->点击i进入输入模式，在输入模式中可以编辑文件内容--->编辑完成之后输入:进入底线命令模式，输入wq保存并退出。

3：vim fax.txt如果fax.txt文件存在就是对文件进行修改，如果fax.txt不存在就创建fax.txt

4：三种模式下常用指令：

- 命令模式： /word 输入字符进行搜索

- 输入模式：输入字符

- 底线命令模式：

  ​                 set nu: 设置行号！

  ​                 wq: 保存并离开

  

## 12：Linux账号管理

>useradd -选项 用户名

1:  -m: 自动创建这个用户的主目录 /home/fax:   

​                       useradd -m  faxgo

2: 本质：Linux中一切皆文件，这里的添加用户说白了就是往某一个文件中写入用户的信息！/etc/passwd中！

>userdel -r faxgo

删除用户的时候将他的目录页一并删除。

>usermod：修改用户

usermod -d  /home/233 faxgo用来指定faxgo的主目录为/home/233

>切换用户

su 用户名

>其他操作

查看主机名：hostname

修改主机名：hostname 要修改的名字

>用户的密码设置问题

1：修改用户密码

​      超级用户： passwd faxgo

​      普通用户：passwd

2：锁定密码

   passwd -l fax   : 锁定之后该用户无法再登录。 

## 13：Linux用户组管理

1：每个用户都有一个用户组，系统可以对一个用户组中的所有用户进行集中管理（开发，测试，运维，root）。用户组的管理涉及用户组的添加，删除和修改。组的添加，删除和修改实际上就是对/etc/group文件的更新。

>/etc/group

1: 创建一个用户组

groupadd -g 666 faxgo:    -g 666表示指定的组faxgo的id为666.不加就默认自增1.

2: groupdel faxgo

3: groupmod -g 666 -n faxfax faxgo

修改用户组的权限信息和名字

4: 切换用户

![1651631560789](Linux.assets/1651631560789.png)

root切换到普通用户：su fax

>/etc/passwd

用户名:密码:用户标识号:组标识号:注释性描述:主目录:登录shell

![1651631859006](Linux.assets/1651631859006.png)

>/etc/shadow

存放用户加密后的的登录密码

## 14：Linux磁盘管理

>df -h

查看所有的磁盘使用情况

>du 

查看当前磁盘使用情况

## 15:  Linux进程管理

### 1：基本概念

- 在Linux中，每一个程序都有一个自己的进程，每一个进程都有一个id号
- 每一个进程都会有一个父进程
- 进程可以有两种存在方式：前台，后台运行
- 一般的话服务都是后台运行的，基本的程序都是前台运行的。

### 2：主要命令

>ps -aux|grep mysql

解释：
      ps: 查看当前系统中正在执行的各种进程信息

​           -a: 显示当前终端运行所有进程的信息。 

​           -u: 以用户的信息显示进程

​           -x:  显示后台运行进程的参数

​     |： 管道符

​     grep: 表示查找文件中符合条件的字符串

>pstree -pu

表示通过目录树结构查看你进程

-p  : 显示父id

-u  : 显示用户组

>kill -9 进程id

结束进程

## 16：环境安装

安装软件一般有三种方式：

- rpm(jdk：在线发布一个SpringBoot项目)
- 解压缩(tomcat,启动并通过外网访问，发布网站)
- yum在线安装(docker：直接安装运行跑起来)

### 1：JDK安装

1：下载JDK

2：安装java环境

```java
1:检查是否有java
  java -version
  rpm -qa|grep  jdk
2:如果有就卸载
  rpm -e --nodeps 卸载内容
3:安装jdk
  rpm -ivk rpm包
4:配置环境变量(在/etc/profile下加入)
  JAVA_HOME=/usr/java/jdk1.8.0_221-amd64
  JRE_HOME=$JAVA_HOME/jre	
  CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib
  PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
  export JAVA_HOME JRE_HOME CLASSPATH PATH
5：激活配置文件
  source /etc/profile
```

3：发布springboot项目

  ```java
1:检查防火墙开放了哪些端口
  firewall-cmd --list-ports
2:开放防火墙的某个端口号
  firewall-cmd --zone=public --add-port=8081/tcp --permanent
3:重启防火墙
  systemctl restart firewalld.service
4:运行项目
  java -jar springboot-04-webdevelop-0.0.1-SNAPSHOT.jar
  ```

4：主机访问

​      直接访问：http://192.168.179.128:8081即可访问到发布的项目

### 2：Tomcat安装

ssm结构的war包就需要放到tomcat中运行！

1：下载tomcat

2：解压这个文件

```java
yum install unzip //安装unzip组件
unzip 文件名.zip  //解压zip文件
```

3：启动tomcat测试

```java
1:开启 ./startup.sh
2:关闭 ./shutdown.sh
```

4：如果8080端口开启了就可以直接访问远程了

​       本机直接访问http://192.168.179.128:8080/即可看到结果

5：后面直接在阿里云上解析域名之后就可以直接使用域名访问。

### 3：Docker安装

```java
步骤：
1：确定是centos7及以上的版本
  cat /etc/redhat-realease
2:yum安装gcc相关
  yum -y install gcc
  yum -y install gcc-c++
3:卸载旧版本
  yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
4:安装需要的软件包
  yum install -y yum-utils device-mapper-persistent-data Ivm2
5:设置stable镜像仓库
  yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
6:更新yum软件包索引
  yum makecache fast
7:安装Docker CE
  yum -y install docker-ce docker-ce-cli containerd.io
8:启动Docker
  systemctl start docker
9:测试
  docker version 查看docker版本
  docker run hello-world 使用docker运行Hello world
  docker images 查看docker的镜像
  
```


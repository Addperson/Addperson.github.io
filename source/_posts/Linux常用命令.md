---
title: Linux常用命令
date: 2019-04-26 11:34:33
tags:
---

# Linux命令学习笔记


## 1. unix和linux

UNIX诞生 

TCPIP协议，c语言诞生

UNIX有很多分支

UNIX发行版本包括linux

linux是开源软件，源代码开放的UNIX

包含一个linux内核，内核版本

厂商下载内核融合其他图形环境  发行版本

所以自己可以开发自己的linux

centOS国内应用多


## 2.开源软件

绝大多数免费 源代码  自由传播，改良，销售

互联网开源技术：

LAMP

Linux 操作系统

Apache web服务器

MySQL 数据库

PHP    编程语言

## 3.应用领域

企业服务器，网站服务器：linux服务器

嵌入式：移动终端:安卓 ios底层都是linux

智能家电 

电影娱乐

## 4.学习方法

windows图形界面 易用性 

linux采用命令行界面 考虑稳定性，安全性

DHCP

>Windows：

系统分区：把硬盘分块，分成小硬盘

高级格式化：写入文件系统。

 1.把分区飞分为小数据块，一般大小4kb，文件存放数据块里。

 2.每个文件有编号，根据标号寻找相应条款，上面记录文件存放相应位置，以此寻找相应的数据块拼凑成文件

编号：Inode号

分区+格式化+分配盘符就可以使用。


>linux：

linux中所有设备都是文件。存放在：/dev/，不同设备有不同目录
 
硬盘设备文件名，分区设备文件名：每个分区定义设备文件名

分区+格式化+分区 建立设备文件名+分配盘符

linux把分配盘符叫做挂载


## linux文件处理命令

命令格式：

命令  [选项]  [参数]

``` bash

ls  -a all所有文件 -l long 所有信息 -d 显示当前目录

mkdir 生成目录  -p在不存在文件下继续生成   

cd   进入

pwd  显示当前目录

rmdir  删除空目录

cp 复制粘贴 -r 可复制目录 -p保留原属性，文件最后操作时间不变 

mv 剪切

rm 删除文件或目录 -r 删除目录  -f强制删除

touch 创建文件

cat 查看文件 tac

more查看多页文件

less可向上翻

head -n查看多少行

tail -n -f动态显示文件内容
```

## 连接命令

```bash
ln  -s 软连接 ，相当于快捷方式

ln  硬连接 同一个文件复制，同步更新 -i相同。删除源文件，硬连接还在

不同：硬连接不可跨分区，不可连接目录
```


## 权限管理命令：

``` bash
chmod  ugoa +-= rwx   改变权限

chmod 777     r=4  w=2  x=1

chmod -R 递归改变目录里所有文件权限

file     r:cat/more/head/tail/less

	 w:vim

	 x:script command

directory   r:ls

            w:mkdir/touch/rmdir/rm

            x:cd


makdir touch 默认权限 755

umask改变默认生成文件权限  chmod chown chgrp
```

## 文件搜索命令

```bash
find [搜索范围] [匹配条件]

find  -name -iname  * ?  

      -size +-   
   
      -user -group
 
      -amin -cmin -mmin

      -type f d l    

      -inum

      -a -o   

      -exec/-ok  命令 {} \;

locate -i  updatedb

which whereis

grep -i -v
```

## 帮助命令：

```bash
man 命令或配置文件 

命令 NAME 作用 、 选项

配置文件 NAME 存放信息  文件格式

whattis 命令简短信息   apropos 配置文件简短信息

命令 --help

info 

help  查看shell内置命令信息
```

## 文件压缩

```bash
zip   -r (压缩目录)  .zip 

unzip

gzip  .gz 压缩

gunzip   解压缩  （gzip -d）

tar -cf -xf   .tar   打包

tar -zcf -zxf  .tar.gz   打包并压缩    解压


bzip2  .bz2  压缩

bunzip2

tar -cjf -xjf    .tar.bz2    打包并压缩    解压
```

## 网络命令

```bash
write  wall 发送信息

last lastlog 查看当前历史用户，最后一次登录时间

ping  traceroute  探测远程主机

netstat 当前网络状态

mount umount ， 挂载命令
```

## 关机重启

```bash
shutdown  [选项] 时间   -c 取消前一个关机命令   -h 关机  -r 重启    

poweroff     halt    init0  关机 

reboot    init6      重启

logout 退出用户
```

## Vim

```bash
vim 文件     命令模式   插入模式   编辑模式

插入命令  aio

定位  :set nu  :n

删除  x nx dd ndd

复制和剪切   yy p   dd p

替换和恢复  r/R  u

搜索和替换   /关键词 n      :范围/要替换关键词/替换关键词/g  或/c

保存和退出  :w  :w 指定文件名     :wq  ZZ   ：q!      ：wq!
```

### vim技巧

导入命令结果   :r! 命令

定义快捷键  ：map 快捷键 触发命令 

连续行注释  ：n1,n2s  / ^  / # /g

            : n1,n2s /^#//g

            :n1,n2s /^/\/\//g

替换 ：ab   mymail  1043844148@qq.com       在vim中写mail自动变为后面1043844148@qq.com


配置文件  .vimrc    /home/username/.vimrc    /root/.vimrc


## 软件包

### 一.rpm包  --源码包经过编译的二进制包

```bash
rpm包   rpm -ivh 包全名  --安装，注意包的依赖性   

rpm -Uvh 包全名  更新    

rpm -e 包名  卸载  

rpm -q 查询已安装包  -l 包中文件 -p未安装包查询  -f 文件属于哪个包  -a所有包

-i详细信息  -R查询包依赖性

rpm2cpio 包全名 |cpio -idv . 文件绝对路径

yum源  --解决包的依赖性，安装过程简单但时间花费增多

yum list  --查看可安装包

yum search 关键字     --通过关键字查找包    

yum -y install   包名   --安装

yum自动安装，不需要考虑依赖性。yum自行下载

yum -y update 包名  --升级

yum -y remove 包名  --自动卸载，把依赖包也都卸载，此依赖包可能用于其他包，所以删除可能造成其他包的崩溃，慎用！！

yum grouplist --列出所有可用软件组

yum grouplist 软件组名 --安装

yum groupremove 软件组名 --卸载
```

### 二.源码包

#### 源码包安装

1，下载压缩包

2，解压缩

3，进入

4，配置 ./configure --prefix==指定路径

5，make

6，makeinstall

#### 脚本包安装

1，下载压缩包

2，解压缩

3，进入

4，运行脚本 ./setup.sh

## 管理命令

### 用户管理 ：

/etc/passwd

用户账户 ： 密码(不显示) ：UID（用户ID）：GID（用户初始组ID) : 说明 ：家目录 ：登陆后shell /bin/bash

man 5 

/etc/shadow 存放密码 

用户名 ：加密密码（！！或* 表示无密码，不能登陆）：最后修改时间 ：修改间隔 ：有效期 ：警告时间 ：到期后宽限时间 ：失效时间（小于等于有效期）：保留字段

### 组管理：

/etc/group

用户创建时生成和用户名一样的用户组，叫初始组，只能有一个。 用户可以添加到其他组获得其他组的权限，可以添加到无限个组中

组名 ：组密码标志 ：GID ：附加用户

/etc/gshadow

组名 ：组密码 ：组管理名 ： 组中附加用户

### 用户家目录 ：

普通用户：/home/用户名/

超级优户：/root/

用户邮箱： /var/spool/mail/用户名/

用户模板目录：/etc/skel/

```bash
useradd 用户名

用户默认值文件 :/etc/default/useradd     /etc/login.defs

passwd [-S查看账户密码信息 -l锁定用户 -u解锁用户 ] 用户名

usermod 改变用户信息， change [-L锁定 -U解锁]改变用户密码信息

userdel 用户名

id 用户名 查看用户相关id

su - （“-”必须加） 用户名 --切换用户

su - root -c “useradd user1” --不切换为root，执行只有root才有权限的命令

groupadd [-g 修改组ID]组名

groupmod [-g ，-n修改组名]组名

groupdel 组名

gpasswd [-a 用户名(用户加入组)，-d用户名(把用户从组中删除)] 组名
```

### 权限管理
 
```bash
ACL权限 ：用于给用户单独设置权限

setfacl [-m u：用户名：权限 （设定权限），-m g：组名：权限 （设定权限）]文件 --设置ACL权限            

setfacl [-m m：权限 （设定权限）]文件   --设置最大ACL权限  mask：

getfacl 用户名 --获取文件ACL权限

setfacl [-x u：用户名，-x g：组名]文件  --删除文件ACL权限

setfacl -b 文件名  --删除本文件所有ACL权限

setfacl [-m u：用户名：权限 （设定权限），-m g：组名：权限 （设定权限）][-R(递归执行，文件夹下所有文件都有ACL权限)]文件

setfacl [-m d:u：用户名：权限 （设定权限）]文件名  --文件夹下的新创建文件都有ACL权限


setUID, 命令执行者操作可执行程序时 ，过程中变为所属者的身份，获得它的权限 chmod 4755 文件名
```

1，可执行程序才能设置

2，执行者对程序有x权限

3，灵魂附体

4，只在命令执行过程中获得

危险setUID，可能会在执行过程中改变系统文件

setUID和setGID针对文件相似，区别是灵魂附体是组，而不是所有者。这两种命令的作用是把一些只有root或者特定用户操作的命令分配给其他用户。比如普通用户可以改密码，普通用户locate查找功能

setGID对目录的作用是创建新文件或目录，所属组变为此目录的所属组。

SBIT粘着位权限，只对目录有效 chmod1755 目录名  chmod o+t 目录名

普通用户对目录有读写权限，在目录中创建新文件。新文件只可以本用户删除，/tmp/就有此权限。

chattr [+-=  i，a]文件或目录

i 锁定文件(对文件只能看不能改，对目录只能修改当前目录中文件内容，对目录不能操作)

a 锁定文件，但只可以往里面增加(对文件只能追加，不能更改删除，对目录里只能增加和修改文件，不允许删除)

### sudo命令：管理员的命令赋予其他用户

visudo命令：改变的是/etc/sudoers配置文件：用户名 ALL=(ALL) 命令（绝对路径）

visudo   --直接修改文件，此命令也可以用vim实现

sudo -l  --查看当前sudo命令

sudo 命令（绝对路径）  --执行root赋予的命令

## 文件系统管理

```bash
df [-a(显示所有文件系统)，-h（习惯的单位容量）] 挂载点  --查看文件系统信息，分区占用情况

du [-a(所有目录)，-h（习惯的单位容量），-s(只统计总大小)] 目录  --查看目录大小

dumpe2fs 分区设备名 --查看分区信息

mount [-l(查看挂载信息)]

mount [-t文件类型，-o特殊选项]设备文件名  挂载点

fdisk -l --查看分区信息
```

分区过程：

1,

-分区：fdisk /dev/sdb（新的硬盘）--手工给新的硬盘分区，用各种命令完成分区过程

-格式化：mkfs  -t ext4 /dev/sdb1   用ext4文件系统格式化分区（分区中建立一个个小格子），（注意不能格式化扩展分区，要格式化扩展分区里面的逻辑分区）

-建立挂载点挂载即可使用  （用命令挂载重启后消失，需要自动挂载）

2,

自动挂载分区：

vim /etc/fstab  修改配置文件  此配置文件在开机启动时根据文件信息自动挂载分区（开机启动默认，改变默认相当于每次开机都自己挂载）

/dev/sdb1   /disk1 挂载点（空目录）         ext4文件系统  1 2

注意：不能写错

如果写错信息，系统启动错误：mount -o remount,rw / --改变根目录权限，挂载写权限（因为文件在/etc/fstab,），有了权限可以修改配置文件，改正确可以运行

如果配置文件根分区信息错误，系统不会启动


分配swap交换分区：

1，free [-m 文件大小为MB]--查看内存和swap信息，使用情况

cached 缓存：读数据更块

buffer 缓冲：写数据更快

2，-按照之前fdisk命令新建swap分区，改变ID为82，（swap专用）
   
   -partprobe

   -格式化：mkswap /dev/sdb6

   -swapon /dev/sdb6  --加入分区  swapon /dev/sdb6  --取消分区     （用命令挂载重启后消失，需要自动挂载）

3，自动挂载分区：

vim /etc/fstab  修改配置文件  

/dev/sdb6   swap 挂载点         swap  0 0 

### rpm包安装的服务启动

#### 独立服务启动

1. /etc/init.d/独立服务名  start|stop|status|restart

2. service 独立服务名  start|stop|status|restart

chkconfig --list   --检查服务启动信息

chkconfig --status-all   --所有rpm安装的服务的状态

#### 独立服务自启动

1.chkconfig --level 2345  独立服务名 on --开启

chkconfig   独立服务名 off  --关闭

2.修改/etc/rc.d/rc.local文件      /etc/rc.d/init.d/httpd start   (服务绝对路径 start)

3.ntsysv命令

#### 基于xinetd服务

1.修改/etc/xinetd.d/telnet   disable=no,
  
  重启service xinetd restart

2.chkconfig telnet on|off

3.ntsysv命令

#### 源码包安装的服务启动

1，绝对路径  start

2.vim  /etc/rc.d/rc.local  服务绝对路径 start

## linux系统管理

### 进程管理

```bash
ps aux --查看所有进程   

pstree

ps -le --查看所有进程

top  --查看健康状态
```
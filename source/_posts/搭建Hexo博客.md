---
title: 搭建Hexo博客

date: 2019-04-02 15:28:40

tags:

---

## 环境准备
1.下载[Nodejs](https://nodejs.org/en/)

![](搭建Hexo博客/markdown-img-paste-20190408113609104.png "下载界面，左边为稳定版，右边为最新版，下载任意一个")

2.进入终端，查看安装是否成功

```bash
node -v

npm -v
```
3.下载cnpm并且安装hexo框架

```bash
npm install -g cnpm --registry=https://registry.npm.taobao.org

cnpm -v                    ----查看安装成功

cnpm install -g hexo-cli   ----安装hexo

hexo -v                    ----查看安装成功

```


## 建立本地博客

1.进入用户家目录（/home/user）,新建文件夹blog

```bash
cd ~

mkdir blog                ----此文件夹就是博客目录，博客资源都在此处

hexo init

```
![](搭建Hexo博客/markdown-img-paste-20190408112917711.png "博客包含内容")

```bash
hexo s            ---启动博客，在本地4000端口打开,如图1
hexo n "test"     ---新建博客文章test
hexo c            ---清除
hexo g            ---生成
hexo s            ---再次启动博客，此时博客更新，如图2

#具体hexo命令介绍可自行查找理解
```
![](搭建Hexo博客/markdown-img-paste-20190408121652468.png)
<center>图1</center>

![](搭建Hexo博客/markdown-img-paste-20190408115636865.png)
<center>图2</center>


## 通过Github部署博客到远端

1.在Github新建仓库，名称必须为：‘用户名’.github.io
2.安装插件：
```bash
cnpm install --save hexo-deployer-git

```
3.配置文件_config.yml,添加到 #Deployment

![](搭建Hexo博客/markdown-img-paste-20190408144220192.png)

4.部署到Github
```bash
hexo d
```
5.浏览器打开 ‘用户名’.github.io

## 主题下载

从网上下载hexo主题的代码到本地，例如：

```bash
git clone https://github.com/litten/hexo-theme-yilia.git
```
此时在blog的theme文件夹下有一个新文件夹yilia，修改配置文件_config.yml
```bash
#Extensions
theme:yilia
```
可以通过上图找到所在位置，修改完毕后，清理生成再部署就会生成新主题

![](搭建Hexo博客/markdown-img-paste-2019040814554139.png)

## 不同电脑操作

### 在建立写博客的电脑操作

### 在另一台电脑的操作


1.搭建本机环境： Nodejs，git hexo框架等

2.把Github上的hexo分支，也就是源文件克隆到本地
3.进入克隆文件内部，内容就是上传的内容，就是在其他电脑上已经记录生成的内容，，如果直接运行hexo命令会出现错误，需要建立本文件内的hexo环境



```bash
git clone -b hexo + 仓库地址

cd  *.github.io --仓库名

npm install hexo --save （如果之前换了cnpm就用cnpm）

npm install

npm install hexo-deployer-git --save



```

此时就可以直接在本地文件夹用hexo命令写博客了，写完部署到远端，同时在用git把本地文件上传到Github仓库的hexo分支，相当于把源代码保存在那里，下次写作合并本地与远端仓库即可。

#### 参考文献
https://www.bilibili.com/video/av44544186?from=search&seid=5533406106430612562

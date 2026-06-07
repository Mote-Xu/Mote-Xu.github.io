---
title: 基于Hexo的博客编写
date: 2024-07-11 05:24:06
tags:
	- 1.安装Git
	- 2.安装Node.js
	- 3.安装Hexo
	- 4.GitHub创建个人仓库
	- 5.生成SSH添加到GitHub
	- 6.将Hexo部署到GitHub
	- 7.发布文章
---

# 常用的Hexo命令：

## 一、初始化和安装

- hexo init [folder]：在指定文件夹初始化一个新的 Hexo 项目。如果不指定文件夹，默认在当前目录下创建。
- npm install：在项目文件夹中运行此命令来安装 Hexo 及其依赖。

## 二、本地开发

- hexo server（简写 hexo s）：启动本地服务器，预览你的网站。
- hexo generate（简写 hexo g）：生成静态文件。
- hexo deploy（简写 hexo d）：部署网站到指定的服务器。
- hexo clean：清除缓存文件 (db.json) 和已生成的静态文件 (public)。

## 三、内容管理

- hexo new [layout] &lt;title&gt;：根据指定的布局（layout），创建一个新的文章。
- hexo publish [layout] &lt;filename&gt;：发布草稿。

## 四、其他常用命令

- hexo list &lt;type&gt;：列出网站中的资料，如：posts, routes 等。
- hexo version：显示 Hexo 的版本。

## 五、帮助与插件

- hexo help：显示帮助信息，列出所有可用的命令和选项。
- hexo plugin list：列出已安装的插件。

# 关于"从本地项目到远程"

```bash
git init #初始化git 生成一个.git文件夹在当前目录,默认创建master分支
git add . #添加文件到暂存区，.代表所有文件
git commit -m "your commit"
git remote add origin <your_ssh_url> #建议使用ssh url,原因下面有讲
git push -u origin master #推送远程，以后用git push就行

```

![](https://cdn.jsdelivr.net/gh/cyan4run/cdn_img/img/202404222338011.png)

![](https://cdn.jsdelivr.net/gh/cyan4run/cdn_img/img/202404222338838.png)


---

# 关于"远程项目到本地工作"

```bash
git clone <http_url OR ssh_url>
cd example #进入项目文件夹
git pull #每次开启你的工作前，检查是否是最新的
git checkout master #切换到master分支
git add . #添加文件到暂存区，.代表所有文件
git commit -m "your commit"
```



但是这时候推送，可能会遇到这样的问题：

鉴权失败：github移除了密码验证

![](https://cdn.jsdelivr.net/gh/cyan4run/cdn_img/img/202404222338241.png)



这个时候实际上就是上文要使用ssh的问题

解决办法如下

```bash
git remote -v #可以看到的确git remote现在是http url 因为clone用的http
git remote rm origin
git reamote add origin git@github.com:cyan4run/example.git #添加ssh的远程
git remote -v #检查一下
```

![](https://cdn.jsdelivr.net/gh/cyan4run/cdn_img/img/202404222338887.png)



然后愉快的推送到仓库

```
git push -u origin master
git push #第一次推送以后以后可以用这个
```

![](https://cdn.jsdelivr.net/gh/cyan4run/cdn_img/img/202404222339907.png)



另外的解决办法是，用token替代你的密码，不介绍了，去setting添加就行



## 附链接

[hexo史上最全搭建教程](https://blog.csdn.net/sinat_37781304/article/details/82729029?app_version=6.3.9&code=app_1562916241&csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%2282729029%22%2C%22source%22%3A%222301_79648754%22%7D&uLinkId=usr1mkqgl919blen&utm_source=app)
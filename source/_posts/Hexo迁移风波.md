---
title: Hexo迁移风波
date: 2018/7/31
categories: Geek
tags: 
	- Hexo
	- git
---


> 前言：之前借助hexo模板搭建了blog，而最近因工作需要，换了新的电脑，才发现使用hexo维护博客极其不方便。想提交博客却只能在下班后在家中电脑上操作，这让我倍感8小时work time的效率出了问题。因为，我觉得，**生活嘛，一定需要紧致感才够过瘾**。

- **主要解决思路：建立git分支，然后利用新分支管理自己博客的hexo源文件**

#### 1. 对username.github.io仓库新建blog分支，并克隆

​	在`username.github.io`仓库上创建一个新分支blog，并切换到该分支下。然后，修改`setting` -> `branches` - > `default branch` 中的默认分支为blog，`update` 更新保存操作。通过` git clone` 命令克隆到本地，进入`username.github.io` 目录。

![blog1](D:\docs\md\imgs\blog1.PNG)



![blog2](D:\docs\md\imgs\blog2.PNG)

#### 2. 将本体hexo 源文件拷贝到 `username.github.io `文件目录中

​	将源电脑中hexo 源文件全部复制拷贝到 `username.github.io` 文件目录下后，将此目录通过git提交到新建立的blog分支上。提交前需注意：**将themes目录下的各个主题目录中的 .git 目录删除（如果有），因为一个git 仓库不能包含另一个主题仓库，否则会提交失败**。

#### 3. 切换到新的工作电脑中进行如下操作

- 将新电脑中添加ssh key 到GitHub账户
- 将`username.github.io` 仓库下的blog新分支克隆到本地
- 切换到`username.github.io`目录下，执行以下命令

``` bash
$ npm install
```

>  如果执行命令提示错误：**npm: command not found** 则需要安装nodejs环境
>
> nodejs安装 （windows下）
>
> 进入  [nodejs 官网](https://nodejs.org/en) 下载nodejs 进行安装，安装完成后运行 `node -v` 检查是否安装成功 

- 使用npm命令安装hexo

```bash
$ npm install -g hexo
```



#### 4. 至此，便可以在新电脑中对博客进行更新和维护操作了

- 使用 Typera 工具编辑文章
- 依次执行 `git add .`、`git commit -m "back to manual blog"`、`git push` 命令
- 最后依次执行 `hexo clean`、 `hexo d -g ` 指令完成博客的部署和发布，此时可以发现，对博客的修改已经同步更新到了master分支，并且两个分支互不干扰。
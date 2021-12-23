---
title: github笔记
tags:
  - git
abbrlink: 1017553822
date: 2021-12-23 13:00:00
---

> github 能干啥 ？它是一个工具，具体来说是版本管理工具。基于这个出发点去思考的话，github似乎也就是做一些版本管理的事儿。

1. 前言
> 首先，你得确保电脑上安装了github。安装方法有很多,github[官方网站](https://www.github.com)

2. 常用命令
~~~ bash
# 初始化
git init

# 配置信息
git config --global user.email "your@example.com"
git config --global user.name "your name"

# 查看当前的状态
git status

# 添加所有文件
git add .

# 添加指定文件
git add xxx.lua

# 提交
git commit -m "日志信息"

# 推送
git push

# 拉取
git pull

# 查看日志
git log 

# 查看日志ref
git reflog

# 回滚
git reset --hard <[git log]后面的全贴上>

# 回滚
git reset --hard <[git reflog]前面的全贴上>


# 分支
#1.切换分支
git checkout master

#2.合并分支
git merge dev

#3.删除分支
git branch -d bug

#4.查看当前分支
git branch

#5.创建分支
git branch bug

# github克隆/推送

#1.给远程仓库起别名
git remote add origin  远程仓库地址

#2.推送
git push
git push -u origin 分支

#3.克隆代码
git clone 远程仓库地址

#4.切换分支
git checkout 分支

#5.资源拉取
git pull
git pull origin 分支

git fetch origin dev
git merge origin/dev

git rebase -i 版本号
git rebase -i HEAD ~3
pick > s

git log --graph --pertty=format:"%h %s"

git pull origin dev

git fetch origin dev
git rebase origin/dev

# 变基
git rebase 分支

# 解决完冲突之后
git rebase --continue

# Beyond Compare
# 1.安装Beyond Compare3

# 2.配置信息
git config --local merge.tool bc3
git config --local mergetool.path '/usr/local/bin/bcomp'
git config --local mergetool.keepBackup false

# 3.应用bc3解决冲突
git mergetool

# tag
git tag -a v2 -m "tag信息"
git push origin --tags

#维护
git clone -b v2 地址

#配置
1.本项目生效 /项目/.git/config
git config --local user.name
git config --local user.emal

2.全局 ~/.gitconfig
git config --global user.name
git config --global user.emal

3.系统 /etc/.gitconfig (sudo权限)
git config --system user.name
git config --system user.emal

# 免密登录
# 1.URL
# 原始地址 https://github.com/yourname/project.git
# 修改地址 https://用户名:密码@github.coim/yourname/project.git

git remote add origin https://用户名:密码@github.coim/yourname/project.git
git push origin master

# 2.SSH实现
# 1.生成公钥和私钥(~/.ssh/id_rsa.pub 目录下 id_rsa.pub 公钥 id_ras私钥)
ssh-keygen -r rsa

# 2.拷贝公钥内容，并设置到github SSH and GPG keys

# 3.在git 本地配置ssh地址
git remote add origin git@github.com:yourname/project.git

git push origin master

# 4.git自动管理凭证
Mac OS X >> 钥匙串

# git忽略文件
# 在项目根目录下创建 .gitignore
```
*.h
xx.h
aa.lua
!a.h
files/
*.py[c|a|d]
.gitignore
```
~~~
参考gitignore[官方网站](https://github.coim/gitub/gitignore)

3. 生成静态网页
> 首先得确保已经安装了最新的node.js.
参考hexo[官方网站](https://hexo.io)
~~~
# 检查node.js版本
node -v

# 检查npm版本
npm -v

# 安装hexo
npm install -g hexo-cli

# 新建一个project
hexo init project

# 进入目录
cd project

# 初始化
npm install

# 启动
hexo server

# 帮助
hexo help
~~~

- 常用命令
~~~ sh
# 新建文章
hexo new "新建文章名字"

# 新建页面
hexo new page "新建页面名字"

# 生产静态页面至 public 目录
hexo generate

# 开启预览访问端口
hexo server

# 部署到github
hexo deploy

# 查看帮助
hexo help

# 查看hexo版本
hexo version
~~~

- 命令缩写
~~~ sh
hexo n # hexo new
hexo g # hexo generate
hexo s # hexo server
hexo d # hexo deploy
~~~

- 组合命令
~~~ sh
hexo s -g # 生成本地预览
hexo d -g # 生成并上传到github
~~~

- 配置文件
1) 在本地生成 ssh key
2) 在github的设置里新增 ssh key
3) 在 _config.yml 文件中新增
~~~ yml
deploy:
  type: git
  repository: git@github.com:yourname/yourname.github.io.git
  branch: master
~~~


[Hexo从0到1搭建技术博客](https://edu.csdn.net/course/detail/35315)

1) 安装hexo-abbrlink插件
~~~sh
	npm install hexo-abbrlink --save
~~~
2) 在 _config.yml 文件中新增
~~~ yml
# permalink: :year/:month/:day/:title/
permalink: posts/:abbrlink.html
abbrlink:
  alg: crc32
  rep: dec
~~~

3) 发布插件


4. 任务管理

- issues
  文档以及任务管理

- wiki
  在线文档

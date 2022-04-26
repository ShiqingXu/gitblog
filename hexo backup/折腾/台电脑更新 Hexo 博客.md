---
title: 多台电脑更新 Hexo 博客
date: 2018-12-24 19:07:01
tags: 折腾

---

有不止一台电脑，所以产生了在不同电脑上更新博客的需求。基本思路是将本地的 Hexo 文件同步到 github 上，然后从另一台电脑 pull 下来，这样保持两台电脑上的文件完全一致。

静态的网页文件存储在 master 分支上，为了避免出错新建一个分支专门用于存储源文件，具体步骤如下：

> 1. 在 github 的 username.github.io 这个repo 上新建一个分支 hexo （或者其它你喜欢的名字），并将 hexo 分支设为默认；
> 2. 将 hexo 分支 clone 到本地；
> 3. 将原Hexo文件夹中的所有文件复制到 username.github.io 本地文件夹，并删除 themes 文件夹中的 .git；
> 4. 运行 git add . | git commit -m "xxx" | git push，将新增的文件夹 push 到 github 上；
> 5. （此时假设新电脑已经安装了Hexo）在新电脑上将 hexo 分支 clone 到本地；
> 6. 在本地文件夹中运行一下 npm install；
> 7. 写文章；
> 8. hexo g -d 之前先运行 git add . 等命令将源码 push 到 github；
> 9. 每次换电脑书写之前，先 git pull，保证本地文件为最新。写完先 push ，保证云端最新。

除了新建一个分支，也可以新建一个 repo，甚至不怕出错的话可以直接利用原 master 分支，道理都是通过 github 来同步源文件。

逻辑很简单，然而操作过程中还是遇到不少错误，踩了一些坑，不懂 git 果然不行。
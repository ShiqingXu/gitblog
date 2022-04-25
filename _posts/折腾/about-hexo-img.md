---
title: 在 Hexo 中使用本地图片
date: 2019-01-28 16:54:10
tags: [折腾,Hexo,图床]
---
写博客难免要插入图片，上一个博客使用七牛云作为图床，此次重新搭建之后发现之前存储在七牛云上的图片都失效了，了解了一下才知道七牛云还是有诸多限制的。并且还要备案之类的，很麻烦。当然也考虑过使用其它一些图床，选择太多以至于很久都没决定用哪一个。要么担心安全性，要么担心稳定性。

考虑过用 github 当图床，找了几篇教程发现都比较麻烦，因此一直拖着，导致前几篇文章都没有用图片。今天突然后知后觉地发现 Hexo 其实是可以用本地图片的。

**资源文件夹**

首先要了解[资源文件夹](https://hexo.io/zh-cn/docs/asset-folders.html)的概念。资源（Asset）代表 `source` 文件夹中除了文章以外的所有文件，例如图片、CSS、JS 文件等。比方说，如果你的Hexo项目中只有少量图片，那最简单的方法就是将它们放在 `source/images` 文件夹中。然后通过类似于 `![](/images/image.jpg)` 的方法访问它们。

直接使用资源文件夹的话，本地图片地址与最终发布的文章中的图片地址是不同的，此处需要借助 [CodeFalling/hexo-asset-image](https://github.com/CodeFalling/hexo-asset-image) 。

**设置步骤**

首先要确保  `_config.yml` 中的 `post_asset_folder` 值为 `True`;

在 Hexo 本地文件夹中运行以下命令：

`npm install hexo-asset-image --save`

此时，hexo new post 会创建的目录结构如下：

```
MacGesture2-Publish
├── apppicker.jpg
├── logo.jpg
└── rules.jpg
MacGesture2-Publish.md
```

这样的目录结构（目录名和文章名一致），只要使用 `![test](MacGesture2-Publish/test.jpg)`就可以插入图片。

下面插入一张图片用于测试，与本文内容无关。

![Let's have dinner](about-hexo-img/dinner.JPG)











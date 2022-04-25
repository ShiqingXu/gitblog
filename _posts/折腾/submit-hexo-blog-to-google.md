---
title: 将 Hexo 博客提交到 google 索引
date: 2019-01-30 17:10:34
tags: [hexo,折腾]
---
博客搭建好后需要提交到搜索引擎才能被收录，以增加站点曝光的机率。由于这个博客是搭建在 github pages 上，而 github 早就屏蔽了百度的爬虫，因此这里就只记录提交到 Google 的过程。如果有被百度索引的需求，可能需要在国内镜像一个站点，本篇就不提了。

**1. 生成站点地图**

在 Hexo 本地目录运行以下命令，安装 Google 的站点地图生成插件：

```
npm install hexo-generator-sitemap --save
```

**2. 修改博客配置文件**

在博客的配置文件  `_config.yml` 添加以下内容：

```
# sitemap
sitemap:
  path: sitemap.xml
```

**3. 生成和部署**

执行生成和部署命令

```
hexo g
hexo d
```

命令执行完成后，网站的 public 目录中已经生成了 `sitemap.xml` 文件，这就是站点地图。站点地图里包含该博客的所有页面链接，Google 通过这个文件来抓取博客页面。

**4. 向Google提交站点**

登录 [Google 网站站长](https://www.google.com/webmasters/#?modal_active=none)， 进入 `serch console`,	点击`添加属性`， 将博客网址提交到Google进行验证。

**5. 添加站点地图**

在`抓取`页面，点击`站点地图`，进行添加。

完成后 Google 即可正常对网站进行索引。
























---
title: chrome 搭配 switchyomega 插件实现翻墙
date: 2019-01-07 17:17:46
tags: proxy
---
以前用 ss 都是启用系统代理，浏览器端不需要进行设置即可翻墙，然而最近遇到的一个问题是需要同时连接 ss 与学校的 vpn，以便在 Google Scholar 搜索到论文后跳转到论文页面进行下载。此时 ss 与学校 vpn 就会产生冲突，要么无法用 Google Scholar 搜索，要么无法通过学校帐户免费下载论文。
解决问题的思路是系统代理由学校 vpn 接管，chrome 通过 switchyoega 插件进行分流，需要翻墙的走 ss ，需要学校 vpn 的走系统代理。

基本设置思路：

switchyomega 插件自带的 proxy profiles 的 Protocol 选择 socks5，server 127.0.0.1，port 1080，auto switch profile 页面添加 rule list url https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt，rule list format 选择，autoproxy，rule list rule 选 proxy，点击应用，然后点击 download profiles 更新一下规则，代理方式选择 auto switch即可。

（此处应有截图然而图床还没找到于是就算了
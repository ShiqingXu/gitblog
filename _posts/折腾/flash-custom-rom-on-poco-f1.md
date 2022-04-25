---
title: 跳过Android开机验证
date: 2019-01-04 21:10:54
tags: Android
---

前段时间入手一台小米 pocophone f1，刷成 lineageos 后开机卡在验证界面，折腾一番后通过另一台安装了ss的手机分享热点的方式完成验证。然而重新刷机后这个方法失效了，不知为何开机后连接Wi-Fi无法设置代理，最终通过其它方式绕过验证。总结一下三种可能有效的方式。

---





> 方法一：手机或电脑分享翻墙网络

win10 下的方法：

ss/ssr勾选“允许其它设备连入”并开启热点，在命令提示符下输入 ipconfig 获得本机的 ipv4 地址，手机连接电脑分享的热点，在Wi-Fi的高级设置中选择手动代理，代理服务器地址填入刚才获取的 ipv4 地址，端口 1080，保存。此时正常情况下手机可以通过电脑的梯子翻墙了，可顺利进行验证。

Android 下的方法：

用另一台 Android 手机安装 proxy server 应用，新建一个 server 获取端口与ip地址，开启热点。需要验证的手机连接该热点，后续操作与在 win10 上一致。

> 方法二： 按顺序点击屏幕的四个角

网上有不少人分享这种方法，据称是从左上角开始以顺时针方向依次点击手机屏幕的四个角，可跳过验证。我尝试多次以失败告终。

> 方法三：通过 adb 命令跳过验证

输入以下 adb 命令：

`adb shell settings put secure user_setup_complete 1` 

`adb shell settings put global device_provisioned 1`

这次刷机就是通过这种方法跳过验证的。

---

此外还有一些常用的命令：

隐藏导航栏：

`adb shell wm overscan 0,0,0,-120`

召回导航栏：

`adb shell wm overscan 0,0,0,0`

消除网络x号：

`adb shell settings put global captive_portal_https_url https://www.google.cn/generate_204`

之后需要开启飞行模式再关闭飞行模式。






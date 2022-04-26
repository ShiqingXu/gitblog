---
title: 解决 pixel2 刷机出现 LoadImageAndAuth Failed 问题
date: 2019-03-12 15:47:49
tags: Android

---

例行给 pixel 刷入安全更新时遭遇了第二次 LoadImageAndAuth Failed 错误，搜索资料后发现可能是由于直接通过工厂镜像中的 flash-all 脚本只能刷入一个 slot，想要刷机成功的话必须 slot A 、slot B 分别刷入。

以上这句话的意思是啥我完全不清楚，还是直接放解决方法吧。

xda论坛上有人做了一个一键脚本，地址在 [这里](https://forum.xda-developers.com/pixel-2-xl/development/tool-deuces-bootloop-recovery-flashing-t3704761)，大概翻译一下

前期准备及需要的工具如下：

1. [下载](https://drive.google.com/drive/folders/1a-g1e5WCmPTx_EMTkUufBrecDmsxTuKq?usp=sharing)一键刷机脚本；
2. [下载](https://developers.google.com/android/images#taimen)工厂镜像；
3. [下载](https://developer.android.com/studio/releases/platform-tools.html) adb 工具包；
4. [下载](https://developer.android.com/studio/run/win-usb.html) usb 驱动；
5. 将 adb 文件夹添加到系统的环境变量；

这个脚本的作用如下：

- 修复无限重启；
- 向 slot A & slot B分别刷入rom；
- 能够与Google提供的任何工厂镜像配合使用；
- 自动检测 booloader 、radio；
- （可选）解锁bootloader；
- （可选）格式化用户数据；

步骤如下：

1. 解压工厂镜像，并继续解压里面的压缩包，共计会出现 21 个 .img 文件；
2. 运行前面下载的 deuce-flash-all 脚本；

遇到错误的解决方法：

- 检验是否将 adb 添加到环境变量，方法见[这里](https://wiki.lineageos.org/adb_fastboot_guide.html)；
- 尝试不同的 USB 口；
- 换一根线（优先使用 USB A，不行再尝试 USB C）；
- 在原厂 Recovery 中擦除用户数据；
- 在安装各种第三方 mod 之前刷入纯净的系统；

此外，作者提醒不要用 USB3.0 口，二要用 2.0，我是用的 Type-C端口，没测试 3.0 是否可以。

正常刷入系统后需要重新刷如 twrp 和 magsik，方法如下：

1. 下载 twrp的zip和img文件，将zip文件放入手机存储中；
2. 下载 magsik的zip文件，放入手机存储；
3. 手机进入 bootloader 模式，运行 fastboot boot xxxx.img 命令，将临时twrp刷入手机，并进入 twrp；
4. 刷入 twrp 和 magsik。

感谢 xda 论坛大神们。
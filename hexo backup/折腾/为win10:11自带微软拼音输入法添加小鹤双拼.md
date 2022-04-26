---
title: 为win10/11自带微软拼音输入法添加小鹤双拼
date: 2022-02-11 14:13:07
tags: 折腾
---

多年以来一直使用小狼毫输入法搭配小鹤双拼来打字，词库和UI已经调教得比较适合自己使用。小狼毫至今是win系统上我喜欢的输入法。然而这个输入法并非开箱即用的，每当换设备就需要花费一定的时间进行折腾。此外在公司的设备上进行调教颇为困难。

很多年前小狼毫在win10上不稳定时，我用了一段时间系统自带的微软拼音输入法，其实非常好用，只有两个问题。一是不支持小鹤双拼，需要自己手动添加方案；二是长得太丑了。

后来多次尝试过手动添加方案，再也没成功过，不管是在win10下还是win11下，手动添加方案的界面上保存按钮总是灰色的，无法点击。简单搜索了一下，原来是可以通过改注册表的方式直接添加的。具体有两种方案。

方案一：

可新建一个文本文档，将以下内容复制进去，保存为.reg文件，并双击运行即可。

```
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\InputMethod\Settings\CHS]
"Enable Cloud Candidate"=dword:00000000
"Enable Dynamic Candidate Ranking"=dword:00000001
"EnableExtraDomainType"=dword:00000001
"Enable self-learning"=dword:00000001
"EnableSmartSelfLearning"=dword:00000001
"EnableLiveSticker"=dword:00000000
"Enable EUDP"=dword:00000001
"Enable Double Pinyin"=dword:00000001
"UserDefinedDoublePinyinScheme0"="小鹤双拼*2*^*iuvdjhcwfg^xmlnpbksqszxkrltvyovt"
"DoublePinyinScheme"=dword:0000000a

```





方案二：

手动添加注册表项目。

1. 打开注册表编辑器；
2. 打开以下路径：`HKEY_CURRENT_USER\Software\Microsoft\InputMethod\Settings\CHS`
3. 新建字符串值，字符串名称为：`UserDefinedDoublePinyinScheme0`，值为：`2*^*iuvdjhcwfg^xmlnpbksqszxkrltvyovt`
4. 退出后进入微软拼音设置，即可看到小鹤双拼方案已存在，选择保存即可。

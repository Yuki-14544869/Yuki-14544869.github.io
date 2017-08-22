---
title: Windows 下利用 Cygwin 搭建 C/C++ 开发环境
date: 2017-08-22 16:30:47
tags:
  - Clion
  - 开发环境
---

暑假学校进行实验室保密检查，把实验室的电脑全部装上了一个影子卫士之类的软件，却莫名其妙的把我的编译环境全部弄坏了，因此选择重装。我的 C 语言 IDE 是 JetBrains 家的 Clion。 Clion 对 MinGW 的支持不是很好，会出现输入回显等奇怪的现象，因此选择 Cygwin。

---
# 下载Cygwin
首先去网站 [Cygwin官网](http://www.cygwin.com/) 下载 Cygwin 的 Windows系统的安装包，32位系统下载steup-x86.exe，64位系统则下载steup-x86_64.exe，界面如下。
![](/Img/2017/08/22/微信截图_20170822163925.png)
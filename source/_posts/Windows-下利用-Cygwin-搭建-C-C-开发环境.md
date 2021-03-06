---
title: Windows 下利用 Cygwin 搭建 C/C++ 开发环境
date: 2017-08-22 16:30:47
tags:
  - Clion
  - 开发环境
---

暑假学校进行实验室保密检查，把实验室的电脑全部装上了一个影子卫士之类的软件，却莫名其妙的把我的编译环境全部弄坏了，因此选择重装。我的 C 语言 IDE 是 JetBrains 家的 Clion。 Clion 对 MinGW 的支持不是很好，会出现输入回显等奇怪的现象，因此选择 Cygwin。

原本网上Cygwin的安装配置教程很多的，也就没想着存档，然而今天想找出来时却发现一夜之间所有教程都不见了，于是便将我好不容易在新浪博客上找到的教程扒出来贴在自己的博客里。

---
# 下载Cygwin
首先去网站 [Cygwin官网](http://www.cygwin.com/) 下载 Cygwin 的 Windows系统的安装包，32位系统下载steup-x86.exe，64位系统则下载steup-x86_64.exe，界面如下。
![](/Img/2017/08/22/微信截图_20170822163925.png)

---
# 安装
1. 双击下载好的Cygwin安装包，出现安装界面，点击下一步。之后出现如下界面，默认为第一个选项，意思是从网络下载并安装（从官网下载的不是完整安装包，只是安装引导程序），第二个选项是仅仅下载不安装，第三个则是从本地安装（意思是已经下载好了需要的安装文件）。我还没有下载好文件，并且要安装，所以选择默认第一项，之后点击下一步。![](/Img/2017/08/22/005VELIygy72bVbRvLMb6.png)

2. 在这里选择安装目录，一般要有一个专门用来作开发工具的安装目录，我这里在为C:\Develop，并在此文件下新建用来安装Cygwin的目录，所以总的目录为C:\Develop\MinGW。选择所有用户，之后点击下一步。![](/Img/2017/08/22/005VELIygy72bVYCn7V77.png)

3. 这里要为将要下载的安装包选择存放位置，我选择在C盘的下载目录。选择好后点击下一步。![](/Img/2017/08/22/005VELIygy72bWapp9K18.png)

4. 选择默认，点击下一步。![](/Img/2017/08/22/005VELIygy72bWjrZswb4.png)

5. 闪过一个页面之后出现如下界面，选择蓝色的网址，这是国内中科大的镜像站，所以网速较快，东北地区的也可以选择上面那一个，是大连东软学院的镜像站，隔得较近，应该比中科大的快。![](/Img/2017/08/22/005VELIygy72bWqnp3Gb0.png)

6. 在这个页面之后，就是最重要的一个地方了，会自动进入下一步。![](/Img/2017/08/22/005VELIygy72bWMUKWq9e.png)

7. 在画红线处分别搜索 gcc-core、gcc-g++、make、gdb、binutils，以上所有项目都在 devel 文件夹下。![](/Img/2017/08/22/005VELIygy72bWVT3Vy54.jpg)

8. 原本的 5.3.0-5 *(版本号变大了是正常的事情，反正是数字就对了)*位置也是 Skip，在点击一次之后，出现如下界面即可，其他的也一样。![](/Img/2017/08/22/005VELIygy72bX5gdUn0b.jpg) **gcc-core**
![](/Img/2017/08/22/005VELIygy72bXmEdje5c.jpg) **gcc-g++**
![](/Img/2017/08/22/005VELIygy72bXuaSZOc0.jpg) **make**
![](/Img/2017/08/22/005VELIygy72bXy1AnVd3.png) **gdb**
![](/Img/2017/08/22/005VELIygy72bXCBtSe2e.jpg) **binutils**

9. 之后点击左下角的下一步。![](/Img/2017/08/22/005VELIygy72bXRyn6i82.jpg)

10. 这里检查要安装的项目，和上面选择的是不一样的，增加了许多相关的文件，不好检查，不过一般没问题，所以直接点击下一步。![](/Img/2017/08/22/005VELIygy72bXYrMjsbe.png)

11. 此时开始下载并安装Cygwin，时间稍微久一点。![](/Img/2017/08/22/005VELIygy72bYiPHYK2a.png)

12. 根据需要是否在桌面（第一项）和开始菜单（第二项）创建快捷方式，因为我不常用终端模式，但有时候可能需要，所以只选择第二项，点击完成。![](/Img/2017/08/22/005VELIygy72bYArRxCa0.png)

13. 将安装目录下的 bin目录 添加到 Path 环境变量。![](/Img/2017/08/22/005VELIygy72bYMYMAN09.png)

---
# 验证安装
验证是否安装成功。打开命令提示符窗口，输入 gcc -v，出现以下情况说明安装成功。![](/Img/2017/08/22/005VELIygy72bYYyi2cc0.jpg)

---
# 参考文献
[Windows下利用Cygwin搭建C/C++开发环境GCC](http://blog.sina.com.cn/s/blog_143cf62360102wrgd.html)
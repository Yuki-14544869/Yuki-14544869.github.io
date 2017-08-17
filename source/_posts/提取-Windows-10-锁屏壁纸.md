---
title: 提取 Windows 10 锁屏壁纸
date: 2017-08-16 19:41:25
tags:
  - Windows
---

Windows  10 有一个叫做 「Windows 聚焦」的功能，会定期精选一些壁纸作为锁屏壁纸。**可惜它并没有提供下载功能**，当你看到一些很漂亮的照片，如何将它保存下来，用作其它壁纸呢？

**按 Win + R，复制引号内的代码输入即可进入锁屏壁纸的存放文件夹。** "%localappdata%\Packages\Microsoft.Windows.ContentDeliveryManager_cw5n1h2txyewy\LocalState\Assets"

![](/Img/2017-08-16_19-53.png)

然后将里面的文件**复制到其他文件夹中**，后缀改成「.jpg」即可正常显示。（请勿在原文件夹中修改。）

如果你不想手动修改，也可以使用批量修改。在文件夹里**新建一个文本文档**，打开在里面输入

```
ren * *.jpg  //每个星号前面都有空格
```

保存，然后**将新建文档后缀名「txt」改成「bat」**，双击运行。

![](/Img/2017-08-16_20-02.png)

同一张图片会有竖屏和横屏两种模式，可以方便地为设置为手机壁纸。需要注意的是，这些文件夹里面也会掺杂一些其它缓存的图片。

---

# 参考文献
[有办法提取 Win 10 的锁屏壁纸吗？| 有轻功 #155](http://mp.weixin.qq.com/s/EgyNnpAUaPH9IpwdLwDxNw)

![](/Img/AppSo.bmp)**微信扫一扫关注 AppSo 公众号**
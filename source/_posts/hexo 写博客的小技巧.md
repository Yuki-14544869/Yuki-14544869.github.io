---
title: hexo 写博客的小技巧
tags: 
  - Hexo
date: 2017-08-12 20:59:07
---
# hexo 写博客的小技巧

## 草稿

草稿相当于很多博客都有的“私密文章”功能。

```bash
hexo new draft "your new article's name"
```

会在 source/_drafts 目录下生成一个 your-new-article-s-name.md 的文件。但是这个文件不会被显示在页面上，链接也访问不到。也就是说如果你想把某一篇文章移除显示，又不舍得删除，可以把它移动到 _drafts 目录中。

如果你希望强行预览草稿，更改配置文件：

```bash
render_drafts:true
```

或者以如下方式启动server：

```bash
hexo server --drafts
```

下面这条命令可以把草稿变成文章：

```bash
hexo publish [layout] filename
```

---

## 修改

### 文章名修改

新建文章的时候不小心写错了文章名，可以在该文件的  md 文件内直接修改 title 值即可。至于该文件的文件名改与不改均可，文件名的作用是作为标识你的文章的id食用的，在地址栏才可以看见。不过这里建议还是修改一下，不然如果有细心的读者就会发现地址栏的文章名与当前文章的文章名不匹配，对于强迫症来说是一件非常痛苦的事情。

## 参考文献

1. [Hexo 入门指南（三） - 文章 & 草稿](http://jingyan.baidu.com/article/63f236280da7770208ab3d27.html)
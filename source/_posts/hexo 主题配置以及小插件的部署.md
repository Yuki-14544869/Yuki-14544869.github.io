---
layout: hexo
title: hexo 主题配置以及小插件的部署
date: 2017-08-12 22:12:54
tags: 
  - Hexo
---

# 设置代码高亮主题
NexT 使用 Tomorrow Theme 作为代码高亮，共有5款主题供你选择。 NexT 默认使用的是 白色的 normal 主题，可选的值有 normal，night， night blue， night bright， night eighties：
![normal](/Img/2017-8-12_22-07-normal.png)
![night](/Img/2017-8-12_22-07-night.png)
![night blue](/Img/2017-8-12_22-07-night blue.png)
![night bright](/Img/2017-8-12_22-07-night bright.png)
![night eighties](/Img/2017-8-12_22-07-night eighties.png)  
更改**主题配置文件** highlight_theme 字段，将其值设定成你所喜爱的高亮主题，例如：

```
highlight_theme: night eighties
```

更改**站点配置文件**  hilight.auto_detect 设置为 true：
```
highlight:
  enable: true
  auto_detect: true
  line_number: true
  tab_replace:
```

# 参考文献
1. [hexo 主题配置](http://theme-next.iissnan.com/theme-settings.html)
2. [hexo中next主题代码高亮无法正常显示，如何解决？](https://www.zhihu.com/question/51705387)
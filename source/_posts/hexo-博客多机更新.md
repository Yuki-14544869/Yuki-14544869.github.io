---
title: hexo 博客多机更新
date: 2017-08-17 11:04:48
tags:
  - Hexo
---

晚上回寝室，想用电脑写博客时发现自己平常随身携带的本子忘记带回寝室了，于是便上网搜索了一下如何使用不同的电脑更新同一个博客，感谢[CrazyMilk](https://www.zhihu.com/people/CrazyMilk)在知乎上提供的方法。

---
**这里假设你已经创建出了自己的博客并希望可以将其修改为适合多机使用的情况，如果没有创建出自己的博客，请参照我的这一篇博客：[使用hexo+github搭建我的个人博客](https://yuki-14544869.github.io/2017/08/10/%E4%BD%BF%E7%94%A8%20hexo-github%20%E6%90%AD%E5%BB%BA%E6%88%91%E7%9A%84%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)**

---
# 一、 创建分支
对你的博客的仓库创建一个新的分支。
![](/Img/2017/08/17/2017-08-17_11-20.jpg)
右击左上角的 Branch ，在弹出的界面的输入框里输入 HEXO 并回车。
![](/Img/2017/08/17/2017-08-17_11-24.jpg)
创建完成之后如下图所示
![](/Img/2017/08/17/2017-08-17_11-22.jpg)

---
# 二、 设置 HEXO 为默认分支
在页面的最上方寻找到Settings选项
![](/Img/2017/08/17/2017-08-17_11-32.jpg)
在左侧选择 Branches 将其中的 Default branch 更改为 HEXO
![](/Img/2017/08/21/20170821213450.png)
回到本仓库的首页，选择 upload 将博客的源文件全部上传至此远程仓库。**此时的分支应为 HEXO**

---
# 三、 下载博客源文件
在自己选定的地方打开 git bash 使用
```
git clone git@github.com:Yuki-14544869/Yuki-14544869.github.io.git //将这里的Yuki-14544869改成你的用户名
```
拷贝仓库

---
# 四、 搭建环境
在下载下来的文件夹下打开 git bash 依次执行,**此时当前分支应显示为 HEXO**
```
npm install hexo
hexo init
npm install
npm install hexo-deployer-git
```

---
# 五、 修改配置
修改**站点配置文件** _deploy 参数，分支应为master

---
# 六、 上传博客源文件
与 git 提交代码的方式无二，依次执行
```
git add .
git commit -m "..."
git push origin HEXO
```
指令将文件推送至 GitHub **此时当前分支应显示为 HEXO**

--
# 七、 更新博客
执行
```
hexo g -d
```
将博客发布

---
这样一来，在GitHub上的[https://github.com/Yuki-14544869/Yuki-14544869.github.io](https://github.com/Yuki-14544869/Yuki-14544869.github.io)仓库就有两个分支，一个hexo分支用来存放网站的原始文件，一个master分支用来存放生成的静态网页。完美( •̀ ω •́ )y！

---
# 参考资料
1. [使用hexo，如果换了电脑怎么更新博客？](https://www.zhihu.com/question/21193762)

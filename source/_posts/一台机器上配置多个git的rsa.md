---
title: 一台机器上配置多个git的rsa
date: 2018-04-28 16:24:38
tags:
    - git
---
# 一台机器上配置多个 git 的 rsa

## 建立 rsa

``` git
ssh-keygen -t rsa -C "你的邮箱地址"
```

执行完这条命令之后, 会弹出如下提示：

``` git
Enter file in which to save the key (/Users/aaaa/.ssh/id_rsa):
```

在这里这里就是 “建立多个不同rsa“文件的地方，输入不同的名字，就会产生不同的rsa.例如输入: github_rsa。就产生了github_rsa.
重复上面的命令，再建立gitlab的即可。

## 修改 ssh config

现在，gitlab和github都有自己的rsa了。那么，如何引导选择不同的rsa验证呢。这时候需要修改 ssh config文件。
如果你的 ~/.ssh 目录下没有 请建立一个这样的文件， 文件名: config。
下面的事情是修改config文件。按照如下方式修改。

``` git
Host github.com
User 你的名字
IdentityFile ~/.ssh/id_rsa

Host gitlab.com
User 你的名字
IdentityFile ~/.ssh/csdn_rsa
```

## 删除本地全局设置

如果之前使用过程中使用过`git config --global user.name`或者 `git config --global user.email` 命令，git 会在 C 盘目下产生一个**.gitconfig**文件，这个文件中保存了全局的git帐号信息，应该删除掉。

## 参考资料

[如何在一台机器上配置多个git的rsa](https://blog.csdn.net/z69183787/article/details/52606453)


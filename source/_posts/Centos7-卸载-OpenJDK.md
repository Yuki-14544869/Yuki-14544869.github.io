---
title: Centos7 卸载 OpenJDK
date: 2018-01-05 15:47:19
tags:
  - Centos
---
# Centos 卸载 OpenJDK

## 查找 OpenJDK 安装包

```bash
[root@localhost ~]# rpm -qa | grep openjdk
java-1.8.0-openjdk-headless-1.8.0.151-5.b12.el7_4.x86_64
java-1.8.0-openjdk-1.8.0.151-5.b12.el7_4.x86_64
```

## 卸载 OpenJDK 安装包

```bash
[root@localhost ~]# yum -y remove java-1.8.0-openjdk-headless-1.8.0.151-5.b12.el7_4.x86_64
[root@localhost ~]# yum -y remove java-1.8.0-openjdk-1.8.0.151-5.b12.el7_4.x86_64
```

## 参考文献

1.[CentOS7卸载OpenJDK安装Oracle JDK](http://blog.csdn.net/zitong_ccnu/article/details/40041533)
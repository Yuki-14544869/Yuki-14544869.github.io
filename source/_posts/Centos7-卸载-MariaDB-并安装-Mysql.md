---
title: Centos7 卸载 MariaDB 并安装 Mysql
date: 2018-01-14 13:10:32
tags:
  - Centos
---
# Centos7 卸载 MariaDB 并安装 Mysql

## 查看已安装的的 MariaDB 相关的模块

```bash
[user@localhost ~]$ rpm -qa | grep mariadb
mariadb-server-5.5.56-2.el7.x86_64
mariadb-5.5.56-2.el7.x86_64
mariadb-libs-5.5.56-2.el7.x86_64
```

## 卸载

```bash
[user@localhost ~]$ sudo rpm -e mariadb-server-5.5.56-2.el7.x86_64
[user@localhost ~]$ sudo rpm -e --nodeps mariadb-5.5.56-2.el7.x86_64
[user@localhost ~]$ sudo rpm -e --nodeps mariadb-libs-5.5.56-2.el7.x86_64
```

## 安装 MySql

```bash
wget 'https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm'
sudo rpm -Uvh mysql57-community-release-el7-11.noarch.rpm
sudo yum install mysql-community-server
sudo systemctl start mysqld
```

## 修改 root 初始密码

MySQL5.7加强了root用户的安全性，因此在第一次安装后会初始化一个随机密码，以下为查看初始随机密码的方式，执行完该命令后则会看到一组随机字符串为初始密码。

```bash
grep 'temporary password' /var/log/mysqld.log
```

### 注意，log只有在mysql服务运行过一遍之后才会有显示

但是不管我怎么操作，在 mysqld.log 中仍然找不到自己的密码，于是，便只能使用终极的破
解操作了

```bash
sudo vim /etc/my.cnf
```

在 [mysqld_safe] 下增加一行

```bash
skip-grant-tables
```

即可跳过授权，直接进入mysql

修改密码

```bash
mysql -uroot
use mysql;
update mysql.user set authentication_string=password('123456') where user='root';
exit
```

此时即可以密码123456来登录 mysql 了

## 增加用户并授予权限

```bash
CREATE USER 'username'@'%' IDENTIFIED BY 'password';
GRANT all privileges ON databasename.tablename TO 'username'@'host'
```

## 参考文献

1.[Centos 7 安装 MySQL](https://www.jianshu.com/p/7cccdaa2d177)
1.[CentOS7.2 安装mysql5.7初始密码问题总结](http://blog.csdn.net/yuxiangjie12/article/details/75452279)
1.[centos7——MySql 5.7添加用户、删除用户与授权](http://www.cnblogs.com/rays-/p/8081798.html)
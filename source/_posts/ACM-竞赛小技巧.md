---
title: ACM 竞赛小技巧
date: 2017-08-23 15:57:24
tags:
  - ACM
  - C++
---
# ACM 竞赛小技巧

## for循环

当使用 for 循环从头至尾去循环一个数组 s 的时候，可以用

```C++
for(int i=0; s[i]; ++i)
```

---

## INF

```C++
const int INF = 0x3f3f3f3f;
```

具体原因参见[为何程序员喜欢将 INF 设置为 0x3f3f3f3f ？](https://yuki-14544869.github.io/2017/08/23/%E4%B8%BA%E4%BD%95%E7%A8%8B%E5%BA%8F%E5%91%98%E5%96%9C%E6%AC%A2%E5%B0%86INF%E8%AE%BE%E7%BD%AE%E4%B8%BA0x3f3f3f3f%EF%BC%9F/)

---

## long long

在计算过程中可以用

```C++
long long ans = 1LL * x * x;
```

将原先被设置成 int 类型的整数转化成 long long 类型。
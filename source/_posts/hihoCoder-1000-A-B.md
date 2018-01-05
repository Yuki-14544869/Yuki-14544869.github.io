---
title: hihoCoder-1000、A + B
date: 2017-08-24 16:17:38
tags:
  - ACM
  - hiho
---
# [#1000 : A + B](http://hihocoder.com/problemset/problem/1000)

## 描述

求两个整数A+B的和

---

## 输入

输入包含多组数据。

每组数据包含两个整数A(1 ≤ A ≤ 100)和B(1 ≤ B ≤ 100)。

---

## 输出

对于每组数据输出A+B的和。

---

## 样例输入

>1 2
3 4

---

## 样例输出

>3
7

---

## 限制

时间限制:10000ms
单点时限:1000ms
内存限制:256MB

---

## 思路

经典题

---

## 题解

### C++

```C++
/*
    Author: Yuki
    GitHub: https://github.com/Yuki-14544869/
    Blog:   https://yuki-14544869.github.io/
*/
#include <bits/stdc++.h>

using namespace std;
const int INF = 0x3f3f3f3f;

int main() {
    int a, b;
    while(cin >> a >> b) {
        cout << a+b << endl;
    }
    return 0;
}
```

### Java

```Java
import java.util.Scanner;

public class Main {
    /*
    Author: Yuki
    GitHub: https://github.com/Yuki-14544869/
    Blog:   https://yuki-14544869.github.io/
    */
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        while(in.hasNext()) {
            int a = in.nextInt();
            int b = in.nextInt();
            System.out.println(a+b);
        }
        in.close();
    }
}
```
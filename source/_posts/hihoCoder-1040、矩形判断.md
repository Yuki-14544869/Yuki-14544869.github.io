---
title: hihoCoder-1040、矩形判断
date: 2017-08-25 15:11:33
tags:
  - ACM
  - 几何
  - hiho
---

# [#1040 : 矩形判断](http://hihocoder.com/problemset/problem/1040)
## 描述
给出平面上4条线段，判断这4条线段是否恰好围成一个面积大于0的矩形。

---
## 输入
输入第一行是一个整数T(1<=T<=100)，代表测试数据的数量。
每组数据包含4行，每行包含4个整数x1, y1, x2, y2 (0 <= x1, y1, x2, y2 <= 100000)；其中(x1, y1), (x2,y2)代表一条线段的两个端点。

---
## 输出

每组数据输出一行YES或者NO，表示输入的4条线段是否恰好围成矩形。

---

## 样例输入
>3
0 0 0 1
1 0 1 1
0 1 1 1
1 0 0 0
0 1 2 3
1 0 3 2
3 2 2 3
1 0 0 1
0 1 1 0
1 0 2 0
2 0 1 1
1 1 0 1

---

## 样例输出
>YES
YES
NO

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
```
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
```
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
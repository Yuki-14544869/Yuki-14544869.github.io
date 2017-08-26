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
#include <map>
#include <set>
#include <cmath>
#include <vector>
#include <string>
#include <iostream>

using namespace std;
typedef long long LL;
const int min = 0x3f3f3f3f;
#define mp make_pair
namespace Geometry {
    struct Point {
        int x, y;
        Point() {}
        Point(int _x, int _y):x(_x), y(_y) {};

        bool operator < (const Point& p) const {
            //优先判断横坐标
            if(x<p.x || (x==p.x&&y<p.y))
                return true;
            return false;
        }

        bool operator == (const Point p) const {
            return (x==p.x && y==p.y);
        }
    };

    struct Line {
        Point a, b;
        double dis;
        double k;
        Line() {}
        Line(Point _a, Point _b):a(_a), b(_b) {
            dis = sqrt((_a.x-_b.x)*(_a.x-_b.x) + (_a.y-_b.y)*(_a.y-_b.y));
        }
    };

    struct Vector {
        Point a, b;
        double dis;
        Vector() {}
        Vector(Point _a, Point _b):a(_a), b(_b) {
            dis = sqrt((_a.x-_b.x)*(_a.x-_b.x) + (_a.y-_b.y)*(_a.y-_b.y));
        }
    };
}
using namespace Geometry;
bool JudgePoint(Line *l) {
    set<Point> p;
    for(int i=0; i<4; ++i) {
        p.insert(l[i].a);
        p.insert(l[i].b);
    }
    return (p.size() == 4);
}
bool JudgeRect(Line *l) {
    for(int i=1; i<4; ++i) {
        //判断是否垂直
        if((l[0].a.y-l[0].b.y)*(l[i].a.y-l[i].b.y) == -(l[0].a.x-l[0].b.x)*(l[i].a.x-l[i].b.x))
            continue;
        //判断是否平行
        if((l[0].a.y-l[0].b.y)*(l[i].a.x-l[i].b.x) == (l[0].a.x-l[0].b.x)*(l[i].a.y-l[i].b.y))
            continue;
        return false;
    }
    return true;
}
int main() {
#ifndef ONLINE_JUDGE
    freopen("in.txt", "r", stdin);
#endif
    int T;
    cin >> T;
    while(T--) {
        Line l[4];
        int tmp1, tmp2, tmp3, tmp4;
        for (int i = 0; i < 4; ++i) {
            cin >> l[i].a.x >> l[i].a.y >> l[i].b.x >> l[i].b.y;
        }
        if(!JudgePoint(l)) {
            cout << "NO" << endl;
            continue;
        } else if(!JudgeRect(l)) {
            cout << "NO" << endl;
            continue;
        } else cout << "YES" << endl;
    }
    return 0;
}


```

### Java
```
Writting
```
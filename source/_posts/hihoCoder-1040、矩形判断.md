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
这道题目思路简单。首先判断给出的四条线段能不能组成四边形，如果可以，在判断这个四边形是不是矩形。 

判断是不是四边形：
输入了四条线段，总共有八个点。如果这八个点中，两两重合，总共有四个点，那么一定是一个四边形。判断八个点是不是两两重合，用set即可。set插入八个点，如果大小为四，那么就是两两重合。
一个四边形，如果一条边和另外三条边要么平行，要么垂直，那么就是矩形。判断平行或垂直，用斜率即可。

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
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Main {
    /*
    Author: Yuki
    GitHub: https://github.com/Yuki-14544869/
    Blog:   https://yuki-14544869.github.io/
    */
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int T = in.nextInt();
        int[][] mat = new int[4][4];
        while(T-- > 0) {
            for(int i=0; i<4; ++i) {
                for(int j=0; j<4; ++j) {
                    mat[i][j] = in.nextInt();
                }
            }
            if(!judgePoint(mat)) {
                System.out.println("NO");
                continue;
            }
            if(!judgeRect(mat))
                System.out.println("NO");
            else System.out.println("YES");
        }
        in.close();
    }

    public static boolean judgePoint(int[][] mat) {
        List<String> points = new ArrayList<String>();
        for(int i=0; i<4; ++i) {
            for(int j=0; j<4; j+=2) {
                String point = String.valueOf(mat[i][j]) + "," + String.valueOf(mat[i][j+1]);
                if(!points.contains(point)) {
                    points.add(point);
                }
            }
        }
        return (points.size() == 4);
    }

    public static boolean judgeRect(int[][] mat) {
        for(int i=1; i<4; ++i) {
            //判断是否垂直
            if((mat[0][1]-mat[0][3])*(mat[i][1]-mat[i][3]) == -(mat[0][0]-mat[0][2])*(mat[i][0]-mat[i][2])){
                continue;
            }
            //判断是否平行
            if((mat[0][1]-mat[0][3])*(mat[i][0]-mat[i][2]) == (mat[0][0]-mat[0][2])*(mat[i][1]-mat[i][3])) {
                continue;
            }
            return false;
        }
        return true;
    }
}

```
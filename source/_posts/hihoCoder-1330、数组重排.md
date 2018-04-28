---
title: hihoCoder - 1330、数组重排
date: 2017-09-12 14:39:29

tags:
 - ACM
 - hiho
---
# [#1330 : 数组重排](http://hihocoder.com/problemset/problem/1330)

## 描述

小Hi想知道，如果他每次都按照一种固定的顺序重排数组，那么最少经过几次重排之后数组会恢复初始的顺序？

具体来讲，给定一个1 - N 的排列 P，小Hi每次重排都是把第 i 个元素放到第 Pi个位置上。例如对于 P = (2, 3, 1)，假设初始数组是(1, 2, 3)，重排一次之后变为(3, 1, 2)，重排两次之后变为(2, 3, 1)，重排三次之后变回(1, 2, 3)。

被排数组中的元素可以认为是两两不同的。

---

## 输入

第一行一个整数 N ，代表数组的长度。 (1 ≤ N ≤ 100)

第二行N个整数，代表1 - N 的一个排列 P 。

---

## 输出

输出最少重排的次数。

---

## 样例输入

>3
2 3 1

---

## 样例输出

>3

---

## 限制

时间限制:10000ms
单点时限:1000ms
内存限制:256MB

---

## 思路

对于每一个点分别通过模拟得出最小步骤，再求每个最小步骤的最小公倍数。

---

## 题解

### C++

```C++
/*
Author: Yuki
GitHub: https://github.com/Yuki-14544869/
Blog:   https://yuki4294967295.cn/
*/
#include <map>
#include <set>
#include <cmath>
#include <queue>
#include <stack>
#include <bitset>
#include <cctype>
#include <cstdio>
#include <vector>
#include <string>
#include <cstring>
#include <utility>
#include <iostream>
#include <algorithm>
using namespace std;
#pragma comment(linker, "/STACK:1024000000,1024000000") //手动扩栈
typedef long long LL;
#define eps 1e-10
#define ff(a, b, c, d) for (int a = b; a < c; a += d)
#define fff(a, b, c, d) for (int a = b; a >= c; a -= d)
#define mm(a, b) memset(a, b, sizeof a)
const double PIE = acos(-1.0);
const int INF = 0x3f3f3f3f;
namespace IO {
const int MX = 4e7;
char buf[MX];
int c, sz;
void init() {
    c = 0;
    sz = fread(buf, 1, MX, stdin);
}
inline bool II(int &t) {
    while(c < sz && buf[c] != '-' && (buf[c] < '0' || buf[c] > '9')) c++;
    if(c >= sz) return false;
    bool flag = 0;
    if(buf[c] == '-') flag = 1, c++;
    for(t = 0; c < sz && '0' <= buf[c] && buf[c] <= '9'; c++) t = t * 10 + buf[c] - '0';
    if(flag) t = -t;
    return true;
}
}
using namespace IO;
void filein() {
    #ifndef ONLINE_JUDGE
        freopen("in.txt", "r", stdin);
    #endif
}

int N;
int p[105] = {0};

LL GCD(LL a, LL b) {
    LL tmp = a%b;
    if(tmp == 0)
        return b;
    return GCD(b, tmp);
}

LL LCM(LL a, LL b) {
    return a*b / GCD(a, b);
}
int main() {
    //ios::sync_with_stdio(false);
    filein();
    //init();
    //II(N);
    while(~scanf("%d", &N)) {
        mm(p, 0);
        ff(i, 1, N+1, 1) {
            scanf("%d", &p[i]);
        }
        LL ans = 1;
        for(LL i=1; i<=N; ++i) {
            LL tmp = p[i];
            LL cnt = 1;
            while(tmp!=i) {
                tmp = p[tmp];
                cnt++;
            }
            ans = LCM(ans, cnt);
        }
        printf("%lld\n", ans);
    }



//    ff(i, 1, N+1, 1) {
//        cout << p[i] << endl;
//    }

    return 0;
}

```

### Java

```java
Writting...
```
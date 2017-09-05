---
title: hihoCoder - 1523、数组重排2
date: 2017-09-05 22:40:07

tags:
 - ACM
 - hiho
 - 贪心
---
# [#1523 : 数组重排2](http://hihocoder.com/problemset/problem/1523)
## 描述
给定一个1-N的排列A1, A2, ... AN，每次操作小Hi可以选择一个数，把它放到数组的最左边。

请计算小Hi最少进行几次操作就能使得新数组是递增排列的。

---
## 输入
第一行包含一个整数N。

第二行包含N个两两不同整数A1, A2, ... AN。(1 <= Ai <= N)

对于60%的数据 1 <= N <= 20

对于100%的数据 1 <= N <= 100000

---
## 输出
一个整数代表答案

---
## 样例输入
>5
2 3 1 4 5

---
## 样例输出
>1

---
## 限制
时间限制:10000ms
单点时限:1000ms
内存限制:256MB

---
## 思路
从数组的最后向前遍历，令flag=n，如果碰见a[i]==n，则n-1。遍历完n即为答案。原理即为此题是将不符合递增序列的数字放置最前方，则必定是将所有不符合序列的数字中最大的一个放到最前，因此只要将符合序列的数字个数找出删去即可。

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
#pragma comment(linker, "/STACK:1024000000,1024000000")     //手动扩栈
typedef long long LL;
#define INF = 0x3f3f3f3f;
#define eps 1e-10
#define ff(a, b, c, d) for(int a=b; a<c; a+=d)
#define fff(a, b, c, d) for(int a=b; a>=c; a-=d)
#define mm(a, b)       memset(a, b, sizeof(a))
const double PIE = acos(-1.0);
void init() {
#ifndef ONLINE_JUDGE
    freopen("in.txt", "r", stdin);
#endif
}


const int N = 100000+50;
int n;
int a[N] = {0};

int main() {
    init();
    cin >> n;
    ff(i,0,n,1)
        cin >> a[i];
    int MAX = n;
    fff(i,n-1,0,1)
        if(a[i] == MAX)
            MAX--;
    cout << MAX << endl;
    return 0;
}
```

### Java
```
Writting...
```
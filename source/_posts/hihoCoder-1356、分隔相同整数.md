---
title: hihoCoder - 1356、分隔相同整数
date: 2017-09-02 20:30:50
tags:
 - ACM
 - hiho
 - 贪心
---
# [#1356 : 分隔相同整数](http://hihocoder.com/problemset/problem/1356)
## 描述
给定一个包含N个整数的数组A。你的任务是将A重新排列，使得任意两个相等的整数在数组中都不相邻。  

如果存在多个重排后的数组满足条件，输出字典序最小的数组。  

这里字典序最小指：首先尽量使第一个整数最小，其次使第二个整数最小，以此类推。

---
## 输入
第一行包含一个整数N，表示数组的长度。(1 <= N <= 100000)  

第二行包含N个整数，依次是 A1, A2, ... AN。(1 <= Ai <= 1000000000)

---
## 输出
输出字典序最小的重排数组。如果这样的数组不存在，输出-1。

---
## 样例输入
>4  
2 1 3 3

---
## 样例输出
>1 3 2 3

---
## 限制
时间限制:10000ms
单点时限:1000ms
内存限制:256MB

---
## 思路
与[#1327 : 分隔相同字符](http://hihocoder.com/problemset/problem/1327)思路类似，只不过因为数据量变大了，无法在时间限制内将数组遍历，于是考虑到了STL用以查询，维护一个二元组（x, y）。有以下集中操作：
1. 插入/删除/修改其中某个元素（x，y）
2. 查询x的最大值
3. 查询y最大的二元组中x最小&次小的那个
4. 查询x最小的二元组

---
## 题解

### C++
```
/*
    Author: Yuki
    GitHub: https://github.com/Yuki-14544869/
    Blog:   https://yuki4294967295.cn/
*/
#include <map>
#include <set>
#include <cmath>
#include <queue>
#include <vector>
#include <string>
#include <cstring>
#include <iostream>
#include <algorithm>
using namespace std;
typedef long long LL;
const int min = 0x3f3f3f3f;
#define ff(a, b, c, d) for(int a=b; a<c; a+=d)
#define mm(a, b)       memset(a, b, sizeof(a))


int N;
map<int, int> cnt;
typedef pair<int, int> p;
set<p, greater<p> > s;


int main() {
#ifndef ONLINE_JUDGE
    freopen("in.txt", "r", stdin);
#endif
    cin >> N;
    int x;
    ff(i, 0, N, 1) {
        cin >> x;
        cnt[x]++;
    }

    for(auto& x : cnt) {
        s.insert({x.second, -x.first});
    }

//    for(auto&x : cnt) {
//        cout << x.first << " " << x.second << endl;
//    }

    if(s.begin()->first > (N-1)/2+1) {
        cout << "-1" << endl;
        return 0;
    }
    //cout << "out : " << N << endl;
    for(int res, pre=0; N--; pre=res) {
        //cout << N << endl;
        int temp = s.begin()->first;
        if(temp > (N-1)/2+1) {
            auto it = s.begin();
            if(it->second == pre)
                it++;
            res = -it->second;
            if(it->first==1)
                cnt.erase(res);
            else {
                s.insert({it->first-1, it->second});
                cnt[res]--;
            }
            s.erase(it);
        } else {
            auto it = cnt.begin();
            if(it->first==pre)
                it++;
            res = it->first;
            s.erase({it->second, -res});
            if(it->second==1)
                cnt.erase(it);
            else {
                it->second--;
                s.insert({it->second, -res});
            }
        }
        cout << res << ' ';
    }
    cout << endl;
    return 0;
}


```

### Java
```
Writting...
```

## 参考材料
[hihocoder 1356 分隔相同整数](http://www.cnblogs.com/Patt/p/5747698.html)
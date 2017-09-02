---
title: hihoCoder - 1327、分隔相同字符
date: 2017-09-02 14:33:04
tags:
 - ACM
 - hiho
 - 贪心
---
# [#1327 : 分隔相同字符](http://hihocoder.com/problemset/problem/1327)
## 描述
给定一个只包含小写字母'a'-'z'的字符串 S ，你需要将 S 中的字符重新排序，使得任意两个相同的字符不连在一起。

如果有多个重排后字符串满足条件，输出字典序最小的一个。

如果不存在满足条件的字符串，输出INVALID。

---
## 输入
字符串S。(1 ≤ |S| ≤ 100000)

---
## 输出

输出字典序最小的答案或者INVALID。

---

## 样例输入
>aaabc

---

## 样例输出
>abaca

---

## 限制
时间限制:10000ms
单点时限:1000ms
内存限制:256MB

---
## 思路
贪心，由题意易知VALID的充要条件即为此字母的长度小于整个字符串长度len/2向上取整。在每次贪心之后重新check新字符串是否VALID就可。

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

string input;
int cnt[26] = {0};

bool check(int x) {
    ff(i, 0, 26, 1)
        if(cnt[i]>(x-1)/2+1)
            return false;
    return true;
}

int main() {
#ifndef ONLINE_JUDGE
    freopen("in.txt", "r", stdin);
#endif
    cin >> input;
    int len = input.size();
    //cout << len << endl;
    ff(i, 0, len, 1)
        cnt[input[i]-'a']++;
    if(!check(len)) {
        cout << "INVALID" << endl;
        return 0;
    }
/*
    int pre = -1;
    ff(i, 0, len, 1) {
        ff(j, 0, 26, 1) {
            if(cnt[j]>0 && j!=pre) {
                cnt[j]--;
                if(check(len-1)) {
                    putchar('a'+j);
                    pre = j;
                    len--;
                    break;
                } else cnt[j]++;
            }
        }
    }
*/

    int pre = -1;
    ff(i, 0, input.size(), 1) {
        ff(j, 0, 26, 1) {
            if(cnt[j] && j!=pre) {
                cnt[j]--;
                if(check(len-1)) {
                    putchar('a'+j);
                    pre=j;
                    len--;
                    break;
                }
                else cnt[j]++;
            }
        }
    }
    cout << endl;
    return 0;
}



```

### Java
```
Writing...
```
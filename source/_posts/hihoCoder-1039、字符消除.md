---
title: hihoCoder-1039、字符消除
date: 2017-08-25 14:02:11
tags:
  - ACM
  - hiho
  - 字符串
---
# [#1039 : 字符消除](http://hihocoder.com/problemset/problem/1039)

## 描述

小Hi最近在玩一个字符消除游戏。给定一个只包含大写字母"ABC"的字符串s，消除过程是如下进行的：

1)如果s包含长度超过1的由相同字母组成的子串，那么这些子串会被同时消除，余下的子串拼成新的字符串。例如"ABCCBCCCAA"中"CC","CCC"和"AA"会被同时消除，余下"AB"和"B"拼成新的字符串"ABB"。
2)上述消除会反复一轮一轮进行，直到新的字符串不包含相邻的相同字符为止。例如”ABCCBCCCAA”经过一轮消除得到"ABB"，再经过一轮消除得到"A"

游戏中的每一关小Hi都会面对一个字符串s。在消除开始前小Hi有机会在s中任意位置(第一个字符之前、最后一个字符之后以及相邻两个字符之间)插入任意一个字符('A','B'或者'C')，得到字符串t。t经过一系列消除后，小Hi的得分是消除掉的字符的总数。

请帮助小Hi计算要如何插入字符，才能获得最高得分。

---

## 输入

输入第一行是一个整数T(1<=T<=100)，代表测试数据的数量。

之后T行每行一个由'A''B''C'组成的字符串s，长度不超过100。

---

## 输出

对于每一行输入的字符串，输出小Hi最高能得到的分数。

---

## 提示

第一组数据：在"ABCBCCCAA"的第2个字符后插入'C'得到"ABCCBCCCAA"，消除后得到"A"，总共消除9个字符(包括插入的'C')。

第二组数据："AAA"插入'A'得到"AAAA"，消除后得到""，总共消除4个字符。

第三组数据：无论是插入字符后得到"AABC","ABBC"还是"ABCC"都最多消除2个字符

---

## 样例输入

>3
ABCBCCCAA
AAA
ABC

---

## 样例输出

>9
4
2

---

## 限制

时间限制:10000ms
单点时限:1000ms
内存限制:256MB

---

## 思路

1. 在给定字符串中的任意位置插入'A'、'B'、'C'中的任意一个字符，然后计算插入后的字符经过消除后最短的字符串长度。
1. 在计算字符消除后最短长度时，通过递归反复计算。
1. 记录每次插入一个字符后经过第2步计算后最短的字符串长度min，最后原字符串的长度-min+1。

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
const int INF=0x3f3f3f3f;

int cal(string p) {
    int len = p.size();
    if(p.empty())
        return 0;
    string t = "";
    int l = 0;
    p += "*";
    for(int i=1; p[i]; i++) {
        if(p[i] != p[i-1]) {
            if(l == i-1) {
                t += p[i-1];
            }
            l = i;
        }
    }
    if(t.size() == len)
        return 0;
    return len-t.size()+cal(t);
}

int main() {
#ifndef ONLINE_JUDGE
    freopen("in.txt", "r", stdin);
#endif
    int t;
    cin >> t;
    while(t--) {
        string s;
        string insert[3] = {"A","B","C"};
        cin >> s;
        int ans=0;
        for(int i=0; s[i]; i++) {
            for(int j=0; j<3; ++j) {
                string tmp = s;
                tmp.insert(i, insert[j]);
                ans = max(ans, cal(tmp));
            }
        }
        cout << ans << endl;
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
        int T = in.nextInt();
        while(T-- > 0) {
            StringBuffer input = new StringBuffer(in.next());
            int ans = 0;
            int len = input.length();
            for(int i=0; i<len; ++i) {
                for(char ch='A'; ch<='C'; ++ch) {
                    StringBuffer tmp = new StringBuffer(input);
                    tmp = tmp.insert(i, ch);
                    ans = Math.max(ans, cal(tmp));
                }
            }
            System.out.println(ans);
        }
        in.close();
    }
    public static int cal(StringBuffer string) {
        int len = string.length();
        if(len<=0)
            return 0;
        StringBuffer buffer = new StringBuffer("");
        int l = 0;
        string.append("*");
        for(int i=1; i<len+1; ++i) {
            if(string.charAt(i) != string.charAt(i-1)) {
                if(l == i-1) {
                    buffer.append(string.charAt(i-1));
                }
                l = i;
            }
        }
        if (buffer.length() == len) {
            return 0;
        }
        return len-buffer.length()+cal(buffer);
    }
}

```
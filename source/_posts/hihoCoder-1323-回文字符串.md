---
title: hihoCoder-1323、回文字符串
tags:
  - ACM
  - hiho
  - DP
  - 字符串
  - C++
date: 2017-08-14 21:26:57
---



# [#1323 : 回文字符串](http://hihocoder.com/problemset/problem/1323)
## 描述
给定一个字符串 S ，最少需要几次增删改操作可以把 S 变成一个回文字符串？

一次操作可以在任意位置插入一个字符，或者删除任意一个字符，或者把任意一个字符修改成任意其他字符。

---
## 输入
字符串 S。S 的长度不超过100, 只包含'A'-'Z'。

---
## 输出
最少的修改次数。

---

## 样例输入
ABAD

---

## 样例输出
1

---

## 限制
时间限制:10000ms  
单点时限:1000ms  
内存限制:256MB

---
## 思路
本题是一道经典动态规划题目。

假设f(s[1..n])表示把长度为n的字符串s改写成回文串需要的操作。  
如果s[1] == s[n]，那么f(s[1..n]) = f(s[2..n-1])。

否则f(s[1..n])是以下三种情况的最小值：  
在s[n]后添加一个字符匹配s[1]，f(s[1..n]) = 1 + f(s[2..n])。
在s[1]前添加一个字符匹配s[n], f(s[1..n]) = 1 + f(s[1..n-1])。
把s[1]和s[n]其中一个修改为另外一个使其匹配，f(s[1..n]) = 1 + f(s[2..n-1])。

改成dp即为：  
仔细分析后发现：  
在字符串头增加一个字符与在字符串尾删去一个字符均是 dp[i][j] = dp[i][j-1] + 1;  
在字符串头删去一个字符与在字符串尾增加一个字符均是 dp[i][j] = dp[i+1][j] + 1;  
在字符串中修改两边中的一个 dp[i][j] = dp[i+1][j-1] + 1;
```
if(s[i]==s[j])
    dp[i][j] = dp[i+1][j-1];
else
    dp[i][j] = min( dp[i+1][j], dp[i][j-1], dp[i+1][j-1] ) + 1;
```

**但是特别注意的一点是dp二维数组的遍历顺序是第一维i从len-1到0，第二维j从i+1到len-1，这样就能保证每次递推都是字符串从i到j的最优情况。**

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

const int  N = 1005;

int dp[N][N] = {0};

int min(const int a, const int b, const int c) {
    return min( a, min( b, c ) );
}

int main() {
    string input;
    cin >> input;
    int len = input.length();
    for (int i=len-1; i>=0; --i) {
        for (int j=i+1; j<len ; ++j) {
            if(input[i]==input[j])
                dp[i][j] = dp[i+1][j-1];
            else
                dp[i][j] = min( dp[i+1][j], dp[i][j-1], dp[i+1][j-1] ) + 1;
        }
    }
    cout << dp[0][len-1] << endl;
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
        char[] s = in.next().toCharArray();
        int dp[][] = new int[1005][1005];
        int len = s.length;
        for(int i=len-1; i>=0; --i) {
            for(int j=i+1; j<len; ++j) {
                if(s[i] == s[j])
                    dp[i][j] = dp[i+1][j-1];
                else
                    dp[i][j] = Math.min(dp[i+1][j], Math.min(dp[i][j-1], dp[i+1][j-1]) ) + 1;
            }
        }
        System.out.println(dp[0][len-1]);
        in.close();
    }
}
```
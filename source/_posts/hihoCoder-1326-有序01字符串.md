---
title: hihoCoder-1326、有序01字符串
date: 2017-08-24 09:14:11
tags:
  - ACM
  - hiho
  - 字符串
  - C++
---



# [#1326 : 有序01字符串](http://hihocoder.com/problemset/problem/1326)
## 描述
对于一个01字符串，你每次可以将一个0修改成1，或者将一个1修改成0。那么，你最少需要修改多少次才能把一个01串 S 变为有序01字符串(有序01字符串是指满足所有0在所有1之前的01串)呢？

---
## 输入
第一行是一个整数 T，代表测试数据的组数。(1 ≤ T ≤ 10)

以下T行每行包含一个01串 S 。(1 ≤ |S| ≤ 1000)

---
## 输出
对于每组测试数据输出最少需要修改的次数。

---
## 样例输入
>3
 000111
 010001
 100000 

---

## 样例输出
>0
 1
 1

---
## 限制
时间限制:10000ms  
单点时限:1000ms  
内存限制:256MB

---
## 思路
最终总会按照某位分段，前面位0，后面为1。那么改动的次数，就是分段的那位前面的1的个数和后面的0的个数的和。统计每一位前面的1的个数个后面的0的个数，找出和的最小值，就可以了。不需要考虑这一位本身是1还是0，因为不管是0还是1都不需要改变。 比如：  
> 字符串 ：        0 0 1 0 1 0 0 1 0 1 1 1 0 1  
  前面的1的个数：   0 0 0 1 1 2 2 2 3 3 4 5 6 6  
  后面的0的个数:    6 5 5 4 4 3 2 2 1 1 1 1 0 0  
  个数和 ：         6 5 5 5 5 5 4 4 4 4 5 6 6 6  

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
    int T;
    cin >> T;
    while(T--) {
        string s;
        cin >> s;
        int len = s.length();
        int ans = INF;
        int cnt0, cnt1;
        for(int i=0; i<=len; ++i) {
            cnt0 = cnt1 = 0;
            for(int j=i-1; j>=0; --j)
                cnt0 += s[j]=='0' ? 0:1;
            for(int j=i; s[j]; ++j)
                cnt1 += s[j]=='1' ? 0:1;
            ans = min(ans, cnt0+cnt1);
        }
        cout << ans << endl;
    }
    return 0;
}
```

### Java
```
import java.util.Scanner;

/*
    Author: Yuki
    GitHub: https://github.com/Yuki-14544869/
    Blog:   https://yuki-14544869.github.io/
*/
public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int T = in.nextInt();
        while(T-- > 0) {
            char[] list = in.next().toCharArray();
            int l = list.length;
            int cnt0, cnt1;
            int ans = 0x3f3f3f3f;
            for(int i=0; i<=l; ++i) {
                cnt0 = cnt1 = 0;
                for(int j=i-1; j>=0; --j) {
                    if(list[j] == '0')
                        cnt0 += 0;
                    else cnt0 += 1;
                }
                for(int j=i; j<l; ++j) {
                    if(list[j] == '1')
                        cnt1 += 0;
                    else cnt1 += 1;
                }
                if(ans > cnt0+cnt1)
                    ans = cnt0+cnt1;
            }
            System.out.println(ans);
        }
        in.close();
    }
}
```
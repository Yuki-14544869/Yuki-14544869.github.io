---
title: hihoCoder-1324、希尔伯特曲线
date: 2017-08-16 23:14:16
tags:
  - ACM
  - hiho
  - 分治
  - 几何
---

# [#1324 : 希尔伯特曲线](http://hihocoder.com/problemset/problem/1324)
## 描述
希尔伯特曲线是以下一系列分形曲线 Hn 的极限。我们可以把 Hn 看作一条覆盖 2n × 2n 方格矩阵的曲线，曲线上一共有 2n × 2n 个顶点(包括左下角起点和右下角终点)，恰好覆盖每个方格一次。

![](/Img/2017/08/13/2017-08-13_23-42.png)

Hn(n > 1)可以通过如下方法构造：

1. 将 Hn-1 顺时针旋转90度放在左下角

2. 将 Hn-1 逆时针旋转90度放在右下角

3. 将2个 Hn-1 分别放在左上角和右上角

4. 用3条单位线段把4部分连接起来

对于 Hn 上每一个顶点 p ，我们定义 p 的坐标是它覆盖的小方格在矩阵中的坐标，定义 p 的序号是它在曲线上从起点开始数第几个顶点。给定 p 的坐标，你能算出 p 的序号吗？ 

---
## 输入
输入包含3个整数 n , x , y 。 n 是分形曲线的阶数，(x, y)是 p 的坐标。

1 ≤ n ≤ 30

1 ≤ x, y ≤ 2n

---
## 输出
p 的序号。

---

## 样例输入
3 6 1


---

## 样例输出
60

---

## 限制
时间限制:10000ms
单点时限:1000ms
内存限制:256MB

---
## 思路
题目中已经说明Hn是由4个Hn-1旋转拼接而成，递归的结构非常明显。所以对于求Hn中(x, y)的序号，我们自然而然会想能否转化成在Hn-1中求(x', y')的序号。

实际上我们只需要考虑Hn中的(x, y)是在左下、左上、右上、右下4个Hn-1中的哪一个里，即可转化成在Hn-1中求(x', y')序号的子问题。具体(x, y)到(x', y')的对应关系涉及到坐标平移和旋转，留给大家思考，不再赘述。

![](/Img/2017/08/16/2017-08-16_19-30.png)

以样例为例，如上图所示，H3中的(6, 1)在右下角的H2中，并且对应着H2中(4, 3)这个点。

如果我们能正确求出H2中(4, 3)这个点的序号是12，又因为前3个H2中一共包含16x3=48个点，那么我们就能求出H3中的(6, 1)的序号是12+48=60。

最后需要注意的是n=30时一共包含2^60个点，所以计算序号的时候需要用64位整型存储。


### 坐标变换
![](/Img/2017/08/24/20170824155059.jpg)
如图，  
当判断点实在当前图形的1位置时，需要将图像对于直线 x=y 进行翻折，即交换x，y的值。  
当判断点实在当前图形的2位置时，只需将图像向下平移即可，即 x 不变，y-m。  
当判断点实在当前图形的3位置时，同样是将图像平移至1位置即可，即  x-m, y-m。  
当判断点实在当前图形的4位置时，先需要将图像平移至1位置,再将图像对于直线 x=-y 进行翻折，即 x=m+1-y, y=2*m+1-x。

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
#define LL long long
using namespace std;
const int INF = 0x3f3f3f3f;
LL HilbertNumber(int n, int x, int y) {
    if(n==0)
        return 1;
    int m = 1<<(n-1);

    if(x<=m) {
        if(y<=m)
            return HilbertNumber(n-1, y, x);
        else
            return 1LL*m*m + HilbertNumber(n-1, x, y-m);
    } else {
        if(y>m)
            return 2LL*m*m + HilbertNumber(n-1, x-m, y-m);
        else
            return 3LL*m*m + HilbertNumber(n-1, m+1-y, 2*m+1-x);
    }
}
int main() {
    int n, x, y;
    cin >> n >> x >> y;
    cout << HilbertNumber(n, x, y) << endl;
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
        int n = in.nextInt();
        int x = in.nextInt();
        int y = in.nextInt();

        System.out.println(HilbertNumber(n, x, y));
        in.close();
    }
    public static long HilbertNumber(int n, int x, int y) {
        if(n==0)
            return 1;
        int m = 1<<(n-1);

        if(x<=m) {
            if(y<=m)
                return HilbertNumber(n-1, y, x);
            else
                return 1L*m*m + HilbertNumber(n-1, x, y-m);
        } else {
            if(y>m)
                return 2L*m*m + HilbertNumber(n-1, x-m, y-m);
            else
                return 3L*m*m + HilbertNumber(n-1, m+1-y, 2*m+1-x);
        }
    }
}
```
---
title: 'hihoCoder - 1519、逃离迷宫II '
date: 2017-09-05 21:42:14

tags:
 - ACM
 - hiho
 - BFS
---
# [#1519 : 逃离迷宫II](http://hihocoder.com/problemset/problem/1519)
## 描述
小Hi被坏女巫抓进里一间有N x M个格子组成的矩阵迷宫。

有些格子是小Hi可以经过的，我们用'.'表示；有些格子上有障碍物小Hi不能经过，我们用'#'表示。小Hi的起始位置用'S'表示，他需要到达用'T'表示的格子才能逃离迷宫。

麻烦的是小Hi被坏女巫施了魔法，他只能选择上下左右某一个方向，沿着这个方向一直走，直到遇到障碍物或者迷宫边界才能改变方向。新的方向可以是上下左右四个方向之一。之后他还是只能沿着新的方向一直走直到再次遇到障碍物或者迷宫边界……  

小Hi想知道他最少改变几次方向才能逃离这个迷宫。

---
## 输入
第一行包含两个整数N和M。  (1 <= N, M <= 500)  

以下N行每行M个字符，代表迷宫。

---
## 输出
一个整数代表答案。如果小Hi没法逃离迷宫，输出-1。

---
## 样例输入
>5 5
S.#.T  
.....  
.....  
.....  
.....

---
## 样例输出
>2

---
## 限制
时间限制:10000ms
单点时限:1000ms
内存限制:256MB

---
## 思路
BFS。往当前方向一直走到无路可走在转弯，一直重复。在节点内用flag标记当前转弯次数。

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
namespace BFS {
    int n, m;
    char maps[505][505];
    bool vis[505][505] = {false};
    int ans[505][505] = {0};
    int sx, sy, ex, ey;
    int dis[4][2] = {-1,0,0,-1,1,0,0,1};//0左1上2右3下
    struct node {
        int x, y;
        int cnt;
        node(int _x, int _y, int _cnt):x(_x),y(_y),cnt(_cnt){}
    };
    bool check(int x, int y) {
        if(x<0 || x>=n || y<0 || y>=m)
            return false;
        return maps[x][y] != '#';
    }
    void init() {
        cin >> n >> m;
        ff(i, 0, n, 1)
            ff(j, 0, m, 1) {
                cin >> maps[i][j];
                if(maps[i][j]=='S')
                    sx=i, sy=j;
                else if(maps[i][j]=='T')
                    ex=i, ey=j;
            }
    }
    int bfs() {
        vis[sx][sy] = true;
        queue<node> q;
        q.push({sx, sy, 0});

        while(!q.empty()) {
            node now = q.front();
            q.pop();

            ff(i, 0, 4, 1) {
                //cout << now.x << " " << now.y << endl;
                int x = now.x + dis[i][0];
                int y = now.y + dis[i][1];
                //cout << x << " " << y << endl;
                if(!check(x, y))
                    continue;
                if(maps[x][y] == 'T')
                    return now.cnt;
                while(check(x+dis[i][0], y+dis[i][1])) {
                    x += dis[i][0];
                    y += dis[i][1];

                    if(x==ex && y==ey)
                        return now.cnt;
                }
                if(!vis[x][y]) {
                    int cnt = now.cnt + 1;
                    q.push((node){x, y, cnt});
                    vis[x][y] = true;
                }
            }
        }
        return -1;
    }
}
using namespace BFS;
void intxt() {
#ifndef ONLINE_JUDGE
    freopen("in.txt", "r", stdin);
#endif
}
int main() {
    intxt();
    init();
//    cout << n << " " << m << endl;
//    ff(i, 0, n, 1) {
//        ff(j, 0, m, 1)cout << maps[i][j];
//        cout << endl;
//    }
//    cout << sx << " " << sy << endl
//         << ex << " " << ey << endl;
    cout << bfs() << endl;
    return 0;
}


```

### Java
```
Writting...
```
---
title: hihoCoder - 1328、逃离迷宫
date: 2017-09-04 21:03:14

tags:
 - ACM
 - hiho
 - BFS
 - 状态压缩
---
# [#1328 : 逃离迷宫](http://hihocoder.com/problemset/problem/1328)
## 描述
小Hi正处在由 N × M 个房间组成的矩阵迷宫中。为了描述方便，我们把左上角的房间的坐标定为(0, 0),右下角房间的坐标定为(N-1, M-1)。每个房间可能是3种状态之一：开放的、关闭的、或者上锁的。

开放房间用'.'表示。小Hi可以从一个开放房间到达另一个相邻的(上下左右)开放房间。

关闭房间用'#'表示。小Hi永远不能进入一个关闭的房间。

上锁的房间用大写字母('A', 'B', 'C' ...)表示。小Hi在取得相应的钥匙前不能进入上锁的房间，而一旦取得钥匙就可以反复进入上锁的房间。每个房间的锁都是不同的，相应的钥匙在迷宫中的某一房间里，小Hi进入该房间就可以取得钥匙。

小Hi一开始处于一个开放房间，坐标(a, b)。迷宫的出口是一个开放或者上锁的房间，坐标(c, d)。假设小Hi每移动到一个相邻房间需要花费单位1的时间，那么小Hi到达出口最少需要花费多少时间？

---
## 输入
第一行包含7个整数: N , M , K , a , b , c , d . 其中N , M是矩阵的行列数；K 是上锁的房间数目，(a, b)是起始位置，(c, d)是出口位置。(1 ≤ N, M ≤ 100, 0 ≤ K ≤ 5, 0 ≤ a, c < N, 0 ≤ b, d < M)

以下 N 行每行包含 M 个字符，表示迷宫矩阵。

再以下 K 行每行两个整数 x, y，依次表示上锁房间A , B , C ....的钥匙所在房间坐标。(0 ≤ x < N, 0 ≤ y < M)

---
## 输出
输出到达出口的最短时间。如果小Hi永远到达不了出口，输出-1。

---
## 样例输入
>4 4 2 0 0 0 3
.A.B
.#..
.#..
.#..
3 0
3 3 

---
## 样例输出
>15

---
## 限制
时间限制:10000ms
单点时限:1000ms
内存限制:256MB

---
## 思路
状态压缩。用v[x][y][k]表示在(x,y)这个点是否访问过，v[x][y][z]的值为当前所花的时间，k的二进制表示现在身上有多少个钥匙。
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

typedef struct node{
    int x, y, sum;
};
char maps[105][105];
int vis[105][105][1<<6];
int dis[4][2] = {-1,0,0,-1,1,0,0,1};
int n, m, k, sx, sy, ex, ey;
vector<pair<int, int>> keys;
bool check(int x, int y) {
    if(x<0 || x>=n || y<0 || y>=n)
        return false;
    if(maps[x][y]=='#')
        return false;

    return true;
}
int bfs() {
    mm(vis, 0);
    vis[sx][sy][0] = 0;
    queue <node> q;
    q.push((node){sx, sy, 0});

    while(!q.empty()) {
        node now = q.front();
        q.pop();
        if(now.x==ex && now.y==ey)
            return vis[now.x][now.y][now.sum];

        ff(i, 0, 4, 1) {
            int nx = now.x+dis[i][0];
            int ny = now.y+dis[i][1];
            if(!check(nx, ny))
                continue;
            if(maps[nx][ny]=='.' && vis[nx][ny][now.sum]==0) {
                vis[nx][ny][now.sum] = vis[now.x][now.y][now.sum]+1;
                q.push((node){nx, ny, now.sum});
            } else if(isdigit(maps[nx][ny])) {
                int sum = now.sum|(1<<(maps[nx][ny]-'0'));
                if(vis[nx][ny][sum])
                    continue;
                vis[nx][ny][sum] = vis[now.x][now.y][now.sum] + 1;
                q.push((node){nx, ny, sum});
            } else if(isupper(maps[nx][ny])) {
                if(now.sum&(1<<(maps[nx][ny]-'A')) && vis[nx][ny][now.sum]==0) {
                    vis[nx][ny][now.sum] = vis[now.x][now.y][now.sum]  + 1;
                    q.push((node){nx, ny, now.sum});
                }
            }
        }
    }
    return -1;
}

int main() {
#ifndef ONLINE_JUDGE
    freopen("in.txt", "r", stdin);
#endif
    cin >> n >> m >> k >> sx >> sy >> ex >> ey;
    ff(i, 0, n, 1)
        ff(j, 0, m, 1)
            cin >> maps[i][j];

    ff(i, 0, k, 1) {
        int x, y;
        cin >> x >> y;
        keys.push_back({x, y});
        maps[x][y] = '0' + i;
    }
    cout << bfs() << endl;
    return 0;
}


```

### Java
```
Writting...
```
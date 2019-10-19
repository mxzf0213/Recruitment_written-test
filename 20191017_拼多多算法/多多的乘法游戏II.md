## 题目描述

皮皮虾轻易通过了多多鸡的乘法游戏之后，多多鸡决定再出一道题目：

给定两个整数A和B，每次可以选择进行如下操作：

1.A‘ = A * 2

2.A' = A * 10 + 1

如果通过若干次上述操作，可以将A变换到B，那么求出最少的操作次数。

## 输入描述

第一行，一个整数T，表示测试用例的组数。（1 <= T <= 100）

第二行开始共T行，每行有两个整数A和B，表示进行游戏的两个数字。

（-1000000000 <= A,B <= 1000000000）

## 输出描述

共T行，每行一个整数，表示A变换到B的最少操作次数。

无解则输出-1。

## 示例1

### 输入

3

1 1

1 22

1 3

### 输出

0

2

-1

## 思路

考虑广度优先搜索。

在* 2和 * 10 + 1的限定下（* 10 + 1很关键！）搜索空间很小，即使是从0开始搜索，也就只有7W空间左右。

## 代码

```c++
#include <bits/stdc++.h>
using namespace std;
const int maxn=5e3+10,mod=1e9+7;
typedef long long ll;
int n,m,k,t;
int main()
{
    int i,j;
    //freopen("in.txt","r",stdin);
    scanf("%d",&t);
    while(t--)
    {
        scanf("%d%d",&n,&m);
        queue<pair<ll,int> >pq;
        pq.push({n,0});
        while(!pq.empty())
        {
            auto x=pq.front();
            if(x.first==m)
            {
                printf("%d\n",x.second);
                break;
            }
            pq.pop();
            if(abs(x.first*2)<=1e9 && x.first)pq.push({x.first*2,x.second+1});
            if(abs(x.first*10+1)<=1e9)pq.push({x.first*10+1,x.second+1});
        }
        if(pq.empty())puts("-1");
    }
    return 0;
}

```


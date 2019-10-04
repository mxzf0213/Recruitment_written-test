## 题目描述

花匠小Q养了两种花，一种红花一种白花，现在小Q用这些花进行摆放。摆放的时候连续的白花的数量只能是k的倍数(倍数可以为0)，不然就会枯萎。

现在给出a和b，小Q想知道长度为[a,b]的摆花方案中合法的摆花方案有多少种呢? （mod 1e9 + 7）

## 输入描述

第一行两个整数t，k。t表示数据组数，k见题意。

接下来t行毎行两个整数，表示a_i，b_i(1 <= a_i <= b_i <= 100000)

## 输出描述

共t行每行一个数表示该[a_i, b_i]下的摆花方案数。

## 示例1

### 输入

3 2

1 3

2 3

4 4

### 输出

6

5

5

### 说明

对于区间[1，3]，合法的方案有:红红红，白白红，红白白，红红，白白，红

对于区间[2，3]，合法的方案有:红红红，白 白红，红白白，红红，白白

对于区间[4，4]，合法的方案有:红红红红，白白白白，白白红红，红红白白，红白白红

## 思路

基础动态规划。

dp[i]表示长度为i的满足条件的摆放的方案数。

转移方程：dp[i] = dp[i-k] + dp[i-1]

对于询问预处理dp数组前缀和，询问时O（1）得到区间和。

## 代码

```c++
#include <bits/stdc++.h>
using namespace std;
const int maxn=1e5+10,mod=1e9+7;
typedef long long ll;
int n,m,k,t;
ll dp[maxn];
int main()
{
    int i,j;
    //freopen("in.txt","r",stdin);
    scanf("%d%d",&t,&k);
    dp[0]=1;
    for(i=0;i<maxn;i++)
    {
        (dp[i+1]+=dp[i])%=mod;
        if(i+k<maxn)
            (dp[i+k]+=dp[i])%=mod;
    }
    for(i=1;i<maxn;i++)
        (dp[i]+=dp[i-1])%=mod;
    while(t--)
    {
        int l,r;
        scanf("%d%d",&l,&r);
        printf("%lld\n",(dp[r]-dp[l-1]+mod)%mod);
    }
    return 0;
}
```


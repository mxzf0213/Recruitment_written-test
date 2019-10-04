## 题目描述

读入一个数列和N值，返回按优先级排序的N个数，满足

(1) 所有偶数优先级大于奇数

(2) 同为偶数或同为奇数时，数值大的优先级高

## 输入描述:

每个测试输入的测试用例，包含一个用半角逗号(，)分开的自然数数列和1个参数N，数列和参数N用半角分号(；)隔开。

这里保证N小于数列的元素个数(不超过100)。

## 输出描述:

在一行内输出N个满足题目条件的自然数，用逗号隔开

## 示例1  

### 输入

555503,772867,756893,339138,399447,40662,859037,628085,855723,974471,599631,636153,581541,174761,948135,411485,554033,858627,402833,546467,574367,360461,566480,755523,222921,164287,420256,40043,977167,543295,944841,917125,331763,188173,353275,175757,950417,284578,617621,546561,913416,258741,260569,630583,252845;10

### 输出

913416,566480,420256,339138,284578,40662,977167,974471,950417,948135

## 思路

自定义结构体，重载<符号，然后快排即可。

## 代码

```c++
#include <bits/stdc++.h>
using namespace std;
const int maxn=1e5+10,mod=1e9+7;
typedef long long ll;
int n,m,k,t;
char a[maxn];
struct node
{
    int v;
    bool operator<(const node&p)const
    {
        if((v^p.v)&1)return v%2 ==0;
        return v>p.v;
    }
};
priority_queue<node>pq;
int b[maxn],all;
int mx;
int main()
{
    int i,j;
    scanf("%s",a);
    for(i=0;a[i];i++)
    {
        if(a[i]==',')continue;
        else if(a[i]==';')
        {
            mx=0;
            i++;
            for(j=i;a[j];j++)
            {
                mx=mx*10+a[j]-'0';
            }
            break;
        }
        int cur=0;
        for(j=i;a[j]!=',' && a[j]!=';';j++)
        {
            cur=cur*10+a[j]-'0';
        }
        b[all++]=cur;
        i=j-1;
    }
    for(i=0;i<all;i++)
    {
        pq.push(node{b[i]});
        if((int)pq.size()>mx)pq.pop();
    }
    vector<int>ret;
    while(!pq.empty())
    {
        ret.push_back(pq.top().v);
        pq.pop();
    }
    reverse(ret.begin(),ret.end());
    bool f=false;
    for(i=0;i<(int)ret.size();i++)
    {
        if(f)printf(",");
        else f=true;
        printf("%d",ret[i]);
    }
    printf("\n");
    return 0;
}
```


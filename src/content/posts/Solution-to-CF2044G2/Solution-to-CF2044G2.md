---
title: Solution to CF2044G
published: 2025-10-20
description: 'a solution to CF2044G Medium Demon Problem'
image: './bg.jpg'
tags: [Informatics,Solutions,Topology,Graph theory]
category: 'Informatics'
draft: false 
lang: ''
---
**This solution will explain the differences between the Easy version and the Hard version.**
## Approach
Consider using topology.  
It's easy to see that the graph in this problem is a **base cycle forest**. For both problems, **once only cycles remain in the graph, no further changes will occur regardless of propagation.**  
Clearly, the time when only cycles remain differs between the two problems.  
In the following, consider the cycles as the roots of trees.  
- For the first problem, since each node only retains one piece of information, the last piece of information a node receives must be **the information from the longest chain**. Thus, the problem transforms into finding the longest chain on the cycle.  
- For the second problem, the received information is unlimited, so it will receive **information from the size of each subtree**. Furthermore, since it only passes one piece of information at a time, the time required to pass all the information is **the sum of the sizes of all subtrees plus itself**.

Using mathematical language would be more intuitive.  
For the first problem, the contribution of a node is:
$$
dp_u=\max(dp_v)+1
$$
For the second problem, the contribution of a node is:
$$
dp_u=\sum{dp_v}+1
$$
Here, $v$ represents the nodes that can reach $u$ in one step.  
It's just a difference in the operator.  
Once a node's answer is updated, it can then update other nodes. Obviously, this problem should be solved using topological sorting.
## AC Code
I have highlighted the differences between the two problems.

**[CF2044G1](https://www.luogu.com.cn/problem/CF2044G1):**
```cpp title="CF2044G1.cpp" {23}
#include<bits/stdc++.h>
#define int long long
#define x first
#define y second
using namespace std;
const int N=2e5+10,inf=0x3f3f3f3f,mod=1e9+7;
typedef unsigned long long ull;
typedef pair<int,int> pii;
typedef long long ll;
/*

*/
int t,n,r[N],d[N],cnt[N],inq[N],ans;
void Solve(){
	cin>>n; ans=0;
	for(int i=1;i<=n;i++) inq[i]=0,d[i]=0,cnt[i]=0;
	for(int i=1;i<=n;i++) cin>>r[i],inq[r[i]]++;
	queue<int> q;
	for(int i=1;i<=n;i++) if(!inq[i]) q.push(i);
	while(!q.empty()){
		int u=q.front(),v=r[u]; q.pop();
		ans=max(ans,++d[u]);
		inq[v]--; d[v]=d[u]; //Here
		if(!inq[v]) q.push(v);
	}
	cout<<ans+2<<"\n";
}
signed main(){
	cin>>t;
	while(t--) Solve();
	return 0;
}
```
**[CF2044G2](https://www.luogu.com.cn/problem/CF2044G2):**
```cpp title="CF2044G2.cpp" {23}
#include<bits/stdc++.h>
#define int long long
#define x first
#define y second
using namespace std;
const int N=2e5+10,inf=0x3f3f3f3f,mod=1e9+7;
typedef unsigned long long ull;
typedef pair<int,int> pii;
typedef long long ll;
/*

*/
int t,n,r[N],d[N],cnt[N],inq[N],ans;
void Solve(){
	cin>>n; ans=0;
	for(int i=1;i<=n;i++) inq[i]=0,d[i]=0,cnt[i]=0;
	for(int i=1;i<=n;i++) cin>>r[i],inq[r[i]]++;
	queue<int> q;
	for(int i=1;i<=n;i++) if(!inq[i]) q.push(i);
	while(!q.empty()){
		int u=q.front(),v=r[u]; q.pop();
		ans=max(ans,++d[u]);
		inq[v]--; d[v]+=d[u]; //Here
		if(!inq[v]) q.push(v);
	}
	cout<<ans+2<<"\n";
}
signed main(){
	cin>>t;
	while(t--) Solve();
	return 0;
}
```

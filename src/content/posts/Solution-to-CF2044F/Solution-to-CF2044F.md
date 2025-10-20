---
title: Solution to CF2044F
published: 2025-10-20
description: 'A solution to CF2044F Easy Demon Problem'
image: './bg.jpg'
tags: [Informatics, Mathematic,Solutions]
category: 'Informatics'
draft: false 
lang: ''
---
### Problem Description
Given two sequences $A$ and $B$, and a two-dimensional array where $a_{i,j} = A_i \times B_j$.  
There are $q$ queries. For each query, given a value $x$, determine whether there exists a pair $(i, j)$ such that after setting all elements in the $i$-th row and $j$-th column to $0$, the sum of all elements in the two-dimensional array equals $x$.

### Solution Idea
Consider the result after removing the $i$-th row and $j$-th column.  
![](https://cdn.luogu.com.cn/upload/image_hosting/gtyt2epx.png)  
As shown in the figure, after removing $(i, j)$, the remaining four parts are combined. The new sum becomes:  
$$
\sum_{p \ne i}{\sum_{q \ne j}{A_p \times B_q}}
$$
This can be separated into:  
$$
\sum_{p \ne i}{A_p} \times \sum_{q \ne j}{B_q}
$$
Let:  
$$
suma = \sum{A_i}, \quad sumb = \sum{B_i}
$$
After preprocessing, the expression becomes:  
$$
(suma - A_i) \times (sumb - B_j)
$$
Thus, the problem reduces to finding factors of $x$.

### Implementation
Store all values of $suma - A_i$ and $sumb - B_j$ in two sets. For each query $x$, check if there exists a factor $p$ of $x$ in one set such that $\frac{x}{p}$ exists in the other set.  
Time complexity: $O(n + m + \sqrt{x})$.

### AC Code
```cpp title="CF2044F.cpp"
#include<bits/stdc++.h>
#define int long long
#define x first
#define y second
using namespace std;
const int N=5e5+10,inf=0x3f3f3f3f,mod=1e9+7;
typedef unsigned long long ull;
typedef pair<int,int> pii;
typedef long long ll;
/*

*/
set<int> ta,tb;
int t,a[N],b[N],n,m,q,suma,sumb;
void Solve(){
	cin>>n>>m>>q; suma=sumb=0;
	for(int i=1;i<=n;i++) cin>>a[i],suma+=a[i];
	for(int i=1;i<=m;i++) cin>>b[i],sumb+=b[i];
	for(int i=1;i<=n;i++) ta.insert(suma-a[i]);
	for(int i=1;i<=m;i++) tb.insert(sumb-b[i]);
	while(q--){
		int x,res;
		cin>>x;
		if(!x){
			cout<<(ta.count(x)||tb.count(x)?"YES":"NO")<<"\n";
			continue;
		}
		bool f=0; res=abs(x);
		for(int i=1;i<=res/i&&!f;i++){
			if(res%i==0){
				if(ta.count(i)&&tb.count(x/i)) f=1;
				if(ta.count(-i)&&tb.count(-x/i)) f=1;
				if(tb.count(i)&&ta.count(x/i)) f=1;
				if(tb.count(-i)&&ta.count(-x/i)) f=1;
			}
		}
		cout<<(f?"YES":"NO")<<"\n";
	}
}
signed main(){
	Solve();
	return 0;
}

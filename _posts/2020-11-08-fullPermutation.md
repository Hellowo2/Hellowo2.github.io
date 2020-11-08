---
title: 全排列
date: 2020-10-26 21:00:14
tags: c语言 算法 递归
coverWidth: 600
coverHeight: 250
---

```c
    一般把1~n这n个整数按某个顺序摆放的结果称为这n个整数的一个排列，而全排列指这n个整数能形成的所有排列。例如对1，2，3这三个整数来说。(1,2,3),(1,3,2),(2,1,3),(2,3,1),(3,1,2),(3,2,1)就是1~3的全排列。现在需要实现按字典序从小到大的顺序输出1~n的全排列。
 ``` 

```c
#include<cstdio>
const int maxn=11;
//P为当前排列.hashtableP记录整数x是否已经在p中 
int n,P[maxn],hashTable[maxn]={false};
//当前处理排列的第index号位 
void generateP(int index)
{
	if(index==n+1)	//递归边界,已经处理完排列的1~n位 
	{
		for(int i=1;i<=n;i++)
		{
			printf("%d",P[i]);	//输出当前排列 
		}
		printf("\n");
		return;
	}
	for(int x=1;x<=n;x++)	//枚举1~n,试图将x填入P[index] 
	{
		if(hashTable[x]==false)	//如果x不在P[0]~P[index-1]中 
		{
			P[index]=x;	//令P的第index位为x,即把x加入当前排列 
			hashTable[x]=true;	//记x已在P中 
			generateP(index+1);	//处理排列的第index+号位 
			hashTable[x]=false;	//已理完P[index]为x的子问题,还原状态 
		}
	}
}

int main()
{
	n=3;	//输出1~3的全排列 
	generateP(1);	//从P[1]开始填 
	return 0;
}

```
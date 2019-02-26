---
layout: post
title: '算法 之 递归'
subtitle: '递归的使用，在双重循环下数字的调换'
date: 2019-02-27
author: CK
categories: 算法
tags: 算法 Tip
---

### 例子1
1,2,3...9 这九个数字组成一个分数，其值恰好为1/3，如何组法？<sup>[[1]](# 附)</sup>


```java
public class T5_1
{
	public static void test(int[] x)
	{
		int a = x[0]*1000 + x[1]*100 + x[2]*10 + x[3];
		int b = x[4]*10000 + x[5]*1000 + x[6]*100 + x[7]*10 + x[8];		
		if(a*3==b) System.out.println(a + " " + b);
	}
	
	public static void f(int[] x, int k)
	{
		if(k>=x.length){
			test(x);
			return;
		}
		
		for(int i=k; i<x.length; i++){
			{int t=x[k]; x[k]=x[i]; x[i]=t;}
			f(x,k+1);
			
			int t=x[k]; x[k]=x[i]; x[i]=t;       // 填空
		}
	}
	
	public static void main(String[] args)
	{
		int[] x = {1,2,3,4,5,6,7,8,9};		
		f(x,0);
	}
}

```


### 例子2
观察下面的加法算式：  
 **祥 瑞 生 辉** + **三 羊 献 瑞 **= **三 羊 生 瑞 气**  
 其中，相同的汉字代表相同的数字，不同的汉字代表不同的数字。<sup>[[1]](# 附)</sup>

```java
class T3_A {
 
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int a[] = new int[8];
		boolean visit[] = new boolean[10];
		dfs(a,visit,0);
		System.out.println("end");
	}
 
	private static void dfs(int[] a, boolean[] visit, int i) {
		// TODO Auto-generated method stub
		if (i==8) {
			judge(a);
			return;
		}
		
		for (a[i] = 0; a[i] < visit.length; a[i]++) {
			if (i==4&&a[4]!=1) {
				continue;
			}
			if (visit[a[i]]==false) {
				visit[a[i]]=true;
				i = i + 1;
				
//				for(int j=0;j<a.length;j++){
//					System.out.println("a["+j+"]="+a[j]+",v["+j+"]="+visit[j]);
//
//				}
				dfs(a, visit, i);
				 
				i = i - 1;
				visit[a[i]]=false;
			}
		}
	}
 
	private static void judge(int[] a) {
		// TODO Auto-generated method stub
		int up = a[0]*1000+a[1]*100+a[2]*10+a[3];
		int down = a[4]*1000+a[5]*100+a[6]*10+a[1];
		int answer = a[4]*10000+a[5]*1000+a[2]*100+a[1]*10+a[7];
		if (up+down==answer) {
			System.out.println(down);//1085
		}
	}
 
}
```



### 附
 >1.第六届蓝桥杯第五题
 >2.第六届蓝桥杯第三题



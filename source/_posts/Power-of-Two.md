---
layout: post
title: Power_of_Two
date: 2016-03-28 18:53:50
categories: [code]
tags: [leetcode,Math,Bit Manipulation]
fullview: 
shortinfo: 
description: 
comments: yes
---

## 题目

Given an integer, write a function to determine if it is a power of two.

## 解题思路

1）递归/循环

2）符合条件的数转换为二进制形式为(100...0)

**注意**

n<=0时的情况要首先排除

## 代码

循环

``` c
bool isPowerOfTwo(int n) {
    if(n<=0)
		return false;
	while(n%2==0){
		n=n/2;
	}
	if(n==1)
		return true;
	return false;
}
```

递归

``` c
bool isPowerOfTwo(int n) {
    if(n<=0)
		return false;
	if(n==1)
		return true;
	if(n%2==0){
		return isPowerOfTwo(n/2);
	}
	return false;
}
```

特别解法

``` c
bool isPowerOfTwo(int n) {
    return (n>0&&!(n&(n-1)));
}
```
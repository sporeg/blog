---
layout: post
title: Power_of_Three
date: 2016-03-28 19:10:05
categories: [code]
tags: [leetcode,Math]
fullview: 
shortinfo: 
description: 
comments: yes
---

## 题目

Given an integer, write a function to determine if it is a power of three.

**Follow up:**

Could you do it without using any loop / recursion?

## 解题思路

1）递归/循环

2）log

3）符合条件的最大数(2^19=1162261467)%符合条件的任意数=0

**注意**

n<=0时的情况要首先排除

## 代码

循环

``` c
bool isPowerOfThree(int n) {
    if(n<=0)
		return false;
	while(n%3==0){
		n=n/3;
	}
	if(n==1)
		return true;
	return false;
}
```

递归

``` c
bool isPowerOfThree(int n) {
    if(n<=0)
		return false;
	if(n==1)
		return true;
	if(n%3==0){
		return isPowerOfThree(n/3);
	}
	return false;
}
```

特别解法

``` c
bool isPowerOfThree(int n) {
    return (n>0&&1162261467%n==0);
}
```
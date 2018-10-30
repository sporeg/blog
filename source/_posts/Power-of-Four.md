---
title: Power_of_Four
date: 2016-04-18 09:56:18
categories: [code]
tags: [leetcode,Bit Manipulation]
comments: yes
layout: post
---

## 题目

Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

**Example:**

Given num = 16, return true. Given num = 5, return false.

**Follow up:** Could you solve it without loops/recursion?

## 解题思路

2的偶数次方

## 代码

```java
public class Solution {
    public boolean isPowerOfFour(int num) {
        return (num>0 && (num&(num-1))==0 && Integer.numberOfTrailingZeros(num)%2==0);
    }
}
```

```java
public boolean isPowerOfFour(int num) {
	return num > 0 && (num&(num-1)) == 0 && (num & 0x55555555) != 0;
	//0x55555555 is to get rid of those power of 2 but not power of 4
	//so that the single 1 bit always appears at the odd position 
}
```
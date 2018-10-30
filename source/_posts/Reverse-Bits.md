---
title: Reverse_Bits
date: 2016-03-30 20:46:56
categories: [code]
tags: [leetcode,Bit Manipulation]
fullview: 
shortinfo: 
description: 
comments: yes
layout: post
---

## 题目

Reverse bits of a given 32 bits unsigned integer.

For example, given input 43261596 (represented in binary as 00000010100101000001111010011100), return 964176192 (represented in binary as 00111001011110000010100101000000).

**Follow up:**

If this function is called many times, how would you optimize it?

## 解题思路

位运算

## 代码

```c
uint32_t reverseBits(uint32_t n) {
    uint32_t num;
	int i;
	for(i=0,num=0;i<32;i++){
	    num = num << 1;
		if(n&1)
			num++;
		n= n >> 1;
	}
	return num;
}
```

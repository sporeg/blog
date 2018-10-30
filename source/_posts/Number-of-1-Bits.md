---
layout: post
title: Number_of_1_Bits
date: 2016-03-28 19:16:30
categories: [code]
tags: [leetcode,Bit Manipulation]
fullview: 
shortinfo: 
description: 
comments: yes
---

## 题目

Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).

For example, the 32-bit integer ’11' has binary representation **00000000000000000000000000001011**, so the function should return 3.

## 解题思路

递归/循环

## 代码

循环

``` c
int hammingWeight(uint32_t n) {
    int i=0;
    if(n==1)
        return 1;
    if(1&n)
        i++;
    while(n=n>>1){
        if(1&n)
            i++;
    }
    return i;
}
```
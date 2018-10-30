---
title: Factorial_Trailing_Zeroes
date: 2016-04-26 15:10:24
categories: [code]
tags: [leetcode,Math]
comments: yes
layout: post
---

## 题目

Given an integer n, return the number of trailing zeroes in n!.

Note: Your solution should be in logarithmic time complexity.

## 解题思路

求n!中因数10的个数=求n!中因数5的个数（因数2个数>>因数5的个数）

## 代码

```java
public class Solution {
    public int trailingZeroes(int n) {
        int num = 0;
        while(n!=0) {
            num += n/5;
            n /= 5;
        }
        return num;
    }
}
```
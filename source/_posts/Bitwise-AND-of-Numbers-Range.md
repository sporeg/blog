---
title: Bitwise_AND_of_Numbers_Range
date: 2016-05-16 10:31:34
categories: [code]
tags: [leetcode,Bit Manipulation]
comments: yes
layout: post
---

## 题目

Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

For example, given the range [5, 7], you should return 4.

## 解题思路

[m,n]中连续两个数(m!=n)，必有1奇1偶，末位AND结果为0

## 代码

```java
public class Solution {
    public int rangeBitwiseAnd(int m, int n) {
        int step = 0;
        while(m != n) {
            m = m >> 1;
            n = n >> 1;
            step++;
        }
        return m << step;
    }
}
```
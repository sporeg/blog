---
title: Climbing_Stairs
date: 2016-04-13 10:02:08
categories: [code]
tags: [leetcode,Dynamic Programming]
comments: yes
layout: post
---

## 题目

You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

## 解题思路

fibonacci数列，注意超时

## 代码

```java
public class Solution {
    public int climbStairs(int n) {
        if(n <= 0)
            return 0;
        if(n == 1)
            return 1;
        if(n == 2)
            return 2;
        int one = 2;
        int two = 1;
        int cur = 0;
        for(int i = 2;i < n;i++) {
            cur = one + two;
            two = one;
            one = cur;
        }
        return cur;
    }
}
```
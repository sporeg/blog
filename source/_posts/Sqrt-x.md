---
title: Sqrt_x
date: 2016-04-07 12:03:12
categories: [code]
tags: [leetcode,Math,Binary Search]
comments: yes
layout: post
---

## 题目

Implement int sqrt(int x).

Compute and return the square root of x.

## 代码

```java
public class Solution {
    public int mySqrt(int x) {
        if(x<=1)
            return x;
        int min = 1;
        int max = x;
        while(min<max) {
            int mid = min + (max - min) / 2;
            if(mid <= x / mid) {
                min = mid + 1;
            } else {
                max = mid;
            }
        }
        return min - 1;
    }
}
```
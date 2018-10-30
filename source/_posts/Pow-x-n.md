---
title: Pow_x_n
date: 2016-04-11 17:48:12
categories: [code]
tags: [leetcode,Math,Binary Search]
comments: yes
layout: post
---

## 题目

Implement _pow(x, n)_.

## 代码

```java
public class Solution {
    public double myPow(double x, int n) {
        if (n == 0)
            return 1;
        if(n < 0) {
            n = -n;
            x = 1/x;
        }
        return x*myPow(x,n-1);
    }
}
```

java.lang.StackOverflowError

```java
public class Solution {
    public double myPow(double x, int n) {
        if (n == 0)
            return 1;
        if(n < 0) {
            n = -n;
            x = 1/x;
        }
        return (n%2==0)?myPow(x*x,n/2):x*myPow(x*x,n/2);
    }
}
```
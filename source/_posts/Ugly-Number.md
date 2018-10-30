---
title: Ugly_Number
date: 2016-04-13 10:11:39
categories: [code]
tags: [leetcode,Math]
comments: yes
layout: post
---

## 题目

Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

Note that 1 is typically treated as an ugly number.

## 解题思路

模运算

> 对于任何同号的两个整数，其取余结果没有争议，所有语言的运算原则都是使商尽可能小。
> 对于异号的两个整数，C++/Java语言的原则是使商尽可能大，很多新型语言和网页计算器的原则是使商尽可能小。

负数模运算结果为负数

```
(-7) = 3 * (-3) + 2
商(-3)小
(-7) = 3 * (-2) + (-1)
商(-2)大
```

## 代码

```java
public class Solution {
    public boolean isUgly(int num) {
        if(num <= 0)
            return false;
        while(num % 2 == 0)
            num = num / 2;
        while(num % 3 == 0)
            num = num / 3;
        while(num % 5 == 0)
            num = num / 5;
        if(num == 1)
            return true;
        return false;
    }
}
```

```java
public class Solution {
    public boolean isUgly(int num) {
        for (int i=2; i<6 && num>0; i++)
            while (num % i == 0)
                num /= i;
        return num == 1;
    }
}
```
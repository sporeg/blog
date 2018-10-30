---
title: Happy_Number
date: 2016-04-13 10:45:16
categories: [code]
tags: [leetcode,Math,Hash Table]
comments: yes
layout: post
---

## 题目

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

**Example:** 19 is a happy number

> 1^2 + 9^2 = 82
> 8^2 + 2^2 = 68
> 6^2 + 8^2 = 100
> 1^2 + 0^2 + 0^2 = 1

## 解题思路

循环即结束

## 代码

```java
public class Solution {
    public boolean isHappy(int n) {
        int fast = n;
        int slow = n;
        while(slow>1) {
            slow = intToNum(slow);
            if(slow == 1)
                return true;
            fast = intToNum(intToNum(fast));
            if(fast == 1)
                return true;
            if(slow == fast)
                return false;
        }
        return true;
    }
    public int intToNum(int n) {
        int num = 0;
        while(n > 0) {
            num = num + (n % 10)*(n % 10);
            n = n / 10;
        }
        return num;
    }
}
```

```java
public class Solution {
    public boolean isHappy(int n) {
        Set<Integer> inLoop = new HashSet<Integer>();
        while(inLoop.add(n)) {
            n = intToNum(n);
            if(n == 1)
                return true;
        }
        return false;
    }
    public int intToNum(int n) {
        int num = 0;
        while(n > 0) {
            num = num + (n % 10)*(n % 10);
            n = n / 10;
        }
        return num;
    }
}
```
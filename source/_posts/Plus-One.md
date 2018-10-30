---
title: Plus_One
date: 2016-04-19 16:59:47
categories: [code]
tags: [leetcode,Array,Math]
comments: yes
layout: post
---

## 题目

Given a non-negative number represented as an array of digits, plus one to the number.

The digits are stored such that the most significant digit is at the head of the list.

## 解题思路

注意类似9 99 999这样需要加长数组的数

## 代码

```java
public class Solution {
    public int[] plusOne(int[] digits) {
        int length = digits.length;
        for(int i=length-1;i>=0;i--) {
            if(digits[i] < 9) {
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }
        int res[] = new int[length+1];
        res[0] = 1;
        return res;
    }
}
```
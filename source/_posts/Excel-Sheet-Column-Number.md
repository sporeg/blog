---
title: Excel_Sheet_Column_Number
date: 2016-04-11 14:00:43
categories: [code]
tags: [leetcode,Math]
comments: yes
layout: post
---

## 题目

Related to question Excel Sheet Column Title

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```

## 解题思路

进制转换

## 代码

```java
public class Solution {
    public int titleToNumber(String s) {
        int length = s.length();
        int num = 0;
        for(int i=0;i<length;i++) {
            num = num*26+(s.charAt(i)-'A'+1);
        }
        return num;
    }
}
```
---
title: Gray_Code
date: 2016-07-11 17:03:00
categories: [code]
tags: [leetcode,Backtracking]
comments: yes
layout: post
---

## 题目
The gray code is a binary numeral system where two successive values differ in only one bit.

Given a non-negative integer n representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.

For example, given n = 2, return [0,1,3,2]. Its gray code sequence is:

```
00 - 0
01 - 1
11 - 3
10 - 2
```

**Note:**

For a given n, a gray code sequence is not uniquely defined.

For example, [0,2,3,1] is also a valid gray code sequence according to the above definition.

## 解题思路

```
/*
 * This function converts an unsigned binary
 * number to reflected binary Gray code.
 *
 * The operator >> is shift right. The operator ^ is exclusive or.
 */
unsigned int binaryToGray(unsigned int num)
{
    return num ^ (num >> 1);
}
```

## 代码

```java
public class Solution {
    public List<Integer> grayCode(int n) {
        List<Integer> res = new LinkedList<>();
        for(int i = 0;i<(1<<n);i++) {
            res.add(i^(i>>1));
        }
        return res;
    }
}
```
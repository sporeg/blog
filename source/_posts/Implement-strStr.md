---
title: Implement_strStr()
date: 2016-05-26 15:39:18
categories: [code]
tags: [leetcode,Two Pointers,String]
comments: yes
layout: post
---

## 题目

Implement strStr().

Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

## 代码

```java
public class Solution {
    public int strStr(String haystack, String needle) {
        int hLength = haystack.length();
        int nLength = needle.length();
        for(int i = 0;i <= hLength; i++) {
            for(int j = 0;j <= nLength;j++) {
                if(j == nLength)
                    return i;
                if(i + j == hLength)
                    return -1;
                if(needle.charAt(j) != haystack.charAt(i + j))
                    break;
            }
        }
        return -1;
    }
}
```
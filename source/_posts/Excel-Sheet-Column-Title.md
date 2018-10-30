---
title: Excel_Sheet_Column_Title
date: 2016-04-11 17:05:55
categories: [code]
tags: [leetcode,Math]
comments: yes
layout: post
---

## 题目

Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:

```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
```

## 代码

```java
public class Solution {
    public String convertToTitle(int n) {
        String title = "";
        while(n!=0) {
            title = (char)((--n)%26+'A') + title;
            n = n / 26;
        }
        return title;
    }
}
```

=========================================================

```java
public class Solution {
    public String convertToTitle(int n) {
        return n==0?"":convertToTitle(--n/26)+(char)(n%26+'A');
    }
}
```
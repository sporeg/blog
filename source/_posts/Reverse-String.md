---
title: Reverse_String
date: 2016-04-25 20:08:04
categories: [code]
tags: [leetcode,Two Pointers,String]
comments: yes
layout: post
---

## 题目

Write a function that takes a string as input and returns the string reversed.

**Example:**

Given s = "hello", return "olleh".

## 代码

```java
public class Solution {
    public String reverseString(String s) {
        char[] string = s.toCharArray();
        int i = 0;
        int j = s.length() - 1;
        while (i < j) {
            char c = string[i];
            string[i] = string[j];
            string[j] = c;
            i++;
            j--;
        }
        return new String(string);
    }
}
```

```java
public class Solution {
    public String reverseString(String s) {
        return  new StringBuilder(s).reverse().toString();
    }
}
```
---
title: Length_of_Last_Word
date: 2016-05-25 15:27:53
categories: [code]
tags: [leetcode,String]
comments: yes
layout: post
---

## 题目

Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

For example, 

Given s = "Hello World",

return 5.

## 代码

```java
public class Solution {
    public int lengthOfLastWord(String s) {
        return s.trim().length()-s.trim().lastIndexOf(" ")-1;
    }
}
```
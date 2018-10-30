---
title: Valid_Anagram
date: 2016-04-11 10:18:31
categories: [code]
tags: [leetcode,Hash Table,Sort]
comments: yes
layout: post
---

## 题目

Given two strings s and t, write a function to determine if t is an anagram of s.

For example,

> s = "anagram", t = "nagaram", return true.
> s = "rat", t = "car", return false.

**Note:**

You may assume the string contains only lowercase alphabets.

**Follow up:**

What if the inputs contain unicode characters? How would you adapt your solution to such case?

## 代码

```java
public class Solution {
    public boolean isAnagram(String s, String t) {
        int[] count = new int[26];
        int length = s.length();
        if(length!=t.length())
            return false;
        for(int i=0;i<length;i++) {
            count[(int)(s.charAt(i)-'a')]++;
            count[(int)(t.charAt(i)-'a')]--;
        }
        for(int i : count) {
            if(i!=0)
                return false;
        }
        return true;
        
    }
}
```
---
title: Reverse_Vowels_of_a_String
date: 2016-04-26 14:53:23
categories: [code]
tags: [leetcode,Two Pointers,String]
comments: yes
layout: post
---

## 题目

Write a function that takes a string as input and reverse only the vowels of a string.

**Example 1:**

Given s = "hello", return "holle".

**Example 2:**

Given s = "leetcode", return "leotcede".

## 代码

```java
public class Solution {
    public String reverseVowels(String s) {
        String vowels = "aeiouAEIOU";
        char[] string = s.toCharArray();
        int i = 0;
        int j = s.length() - 1;
        while (i < j) {
            while(i < j && !vowels.contains(string[i]+""))
                i++;
            while(i < j && !vowels.contains(string[j]+""))
                j--;
            if(i >= j)
                break;
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

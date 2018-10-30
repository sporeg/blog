---
title: Regular_Expression_Matching
date: 2016-05-23 10:19:33
categories: [code]
tags: [leetcode,Dynamic Programming,Backtracking,String]
comments: yes
layout: post
---

## 题目

Implement regular expression matching with support for '.' and '*'.

```
'.' Matches any single character.
'*' Matches zero or more of the preceding element.

The matching should cover the entire input string (not partial).

The function prototype should be:
bool isMatch(const char *s, const char *p)

Some examples:
isMatch("aa","a") → false
isMatch("aa","aa") → true
isMatch("aaa","aa") → false
isMatch("aa", "a*") → true
isMatch("aa", ".*") → true
isMatch("ab", ".*") → true
isMatch("aab", "c*a*b") → true
```

## 代码

```java
public class Solution {
    public boolean isMatch(String s, String p) {
        int pLength = p.length();
        for(int i=0;i<pLength;s = s.substring(1)) {
            char c = p.charAt(i);
            if(i+1 >= pLength || p.charAt(i + 1) != '*') {
                i++;
            } else if(isMatch(s,p.substring(i + 2))) {
                return true;
            }
            if(s.isEmpty() || (c != '.' && c != s.charAt(0))) {
                return false;
            }
        }
        return s.isEmpty();
    }
}
```
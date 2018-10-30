---
title: Word_Break
date: 2016-05-17 15:40:52
categories: [code]
tags: [leetcode]
comments: yes
layout: post
---

## 题目

Given a string s and a dictionary of words dict, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

For example, given

s = "leetcode",

dict = ["leet", "code"].

Return true because "leetcode" can be segmented as "leet code".

## 代码

```java
public class Solution {
    public boolean wordBreak(String s, Set<String> wordDict) {
        int length = s.length();
        boolean flags[] = new boolean[length+1];
        flags[0] = true;
        for(int tail = 1;tail <= length;tail++) {
            for(int head = 0;head < tail;head++) {
                if(flags[head] && wordDict.contains(s.substring(head,tail))) {
                    flags[tail] = true;
                    break;
                }
            }
        }
        return flags[length];
    }
}
```

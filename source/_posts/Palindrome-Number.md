---
title: Palindrome_Number
date: 2016-04-27 17:07:47
categories: [code]
tags: [leetcode,Math]
comments: yes
layout: post
---

## 题目

Determine whether an integer is a palindrome. Do this without extra space.

**Some hints:**

Could negative integers be palindromes? (ie, -1)

If you are thinking of converting the integer to string, note the restriction of using extra space.

You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?

There is a more generic way of solving this problem.

## 代码

```java
public class Solution {
    public boolean isPalindrome(int x) {
        if(x < 0 || (x != 0 && x % 10 == 0))
            return false;
        int y = 0;
        while(x > y) {
            y = y * 10 + x % 10;
            x /= 10;
        }
        return (y == x) || (y/10 == x);
    }
}
```

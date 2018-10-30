---
title: Valid_Parentheses
date: 2016-03-31 20:19:28
categories: [code]
tags: [leetcode,Stack,String]
comments: yes
layout: post
---

## 题目

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.

## 解题思路

堆栈

## 代码

```java
public class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for(int i = 0; i<s.length(); i++) {
            switch (s.charAt(i)) {
                case '(':
                case '[':
                case '{':
                    stack.push(s.charAt(i));
                    break;
                case ')':
                    if(stack.empty() || stack.peek() != '(')
                        return false;
                    stack.pop();
                    break;
                case ']':
                    if(stack.empty() || stack.peek() != '[')
                        return false;
                    stack.pop();
                    break;
                case '}':
                    if(stack.empty() || stack.peek() != '{')
                        return false;
                    stack.pop();
                    break;
            }
        }
        // return true if no open parentheses left in stack
        return stack.empty();
    }
}
```

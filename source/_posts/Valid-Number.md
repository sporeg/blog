---
title: Valid_Number
date: 2016-04-07 15:38:55
categories: [code]
tags: [leetcode,Math,String]
comments: yes
layout: post
---

## 题目

Validate if a given string is numeric.

Some examples:

"0" => true

" 0.1 " => true

"abc" => false

"1 a" => false

"2e10" => true

**Note:** It is intended for the problem statement to be ambiguous. You should gather all requirements up front before implementing one.

## 解题思路

设置三个标志位

*	数字（e后重置）
*	科学计数e
*	小数点dot

## 代码

```java
public class Solution {
    public boolean isNumber(String s) {
        s = s.trim();
        boolean number = false;
        boolean e = false;
        boolean dot = false;
        for(int i = 0; i< s.length();i++) {
            Character c = s.charAt(i);
            if('0' <= c && c <= '9') {
                number = true;
            }else if(c=='.') {
                if(dot || e) {
                    return false;
                }
                dot = true;
            }else if(c=='e') {
                if(e || !number) {
                    return false;
                }
                e = true;
                number = false;
            }else if(c=='-' || c=='+') {
                if(i!=0 && s.charAt(i-1)!='e') {
                    return false;
                }
            }else {
                return false;
            }
        }
        return number;
    }
}
```
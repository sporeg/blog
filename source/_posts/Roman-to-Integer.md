---
title: Roman_to_Integer
date: 2016-04-11 14:42:54
categories: [code]
tags: [leetcode,Math,String]
comments: yes
layout: post
---

## 题目

Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

## 解题思路

|罗马字母|对应值|
|:---:|:---:|
|I|1|
|V|5|
|X|10|
|L|50|
|C|100|
|D|500|
|M|1000|

右>左 减

右≤左 加

## 代码

```java
public class Solution {
    public int romanToInt(String s) {
        HashMap<Character,Integer> map = new HashMap<>();
        map.put('I',1);
        map.put('V',5);
        map.put('X',10);
        map.put('L',50);
        map.put('C',100);
        map.put('D',500);
        map.put('M',1000);
        int length = s.length();
        int num = map.get(s.charAt(length-1));
        int right = num;
        for(int i = length-2;i>=0;i--) {
            int left = map.get(s.charAt(i));
            if(right>left) {
                num-=left;
            }else {
                num+=left;
            }
            right = left;
        }
        return num;
    }
}
```
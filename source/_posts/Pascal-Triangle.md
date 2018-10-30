---
title: Pascal‘s_Triangle
date: 2016-04-21 09:43:08
categories: [code]
tags: [leetcode,Array]
comments: yes
layout: post
---

## 题目

Given numRows, generate the first numRows of Pascal's triangle.

For example, given numRows = 5,

Return

```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

## 代码

```java
public class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> allRows = new ArrayList<List<Integer>>();
        if(numRows == 0)
            return allRows;
        for(int i = 0; i < numRows; i++) {
            List<Integer> row = new ArrayList<Integer>();
            for(int j = 0; j<= i; j++) {
                if(j == 0 || j == i) {
                    row.add(1);
                } else {
                    row.add(allRows.get(i-1).get(j-1) + allRows.get(i-1).get(j));   
                }
            }
            allRows.add(row);
        }
        return allRows;
    }
}
```

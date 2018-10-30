---
title: Same_Tree
date: 2016-04-11 10:05:48
categories: [code]
tags: [leetcode,Tree,Depth-first Search]
comments: yes
layout: post
---

## 题目

Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

## 代码

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(null==p&&null==q)
            return true;
        if((null==p&&null!=q)||(null!=p&&null==q))
            return false;
        if(p.val!=q.val)
            return false;
        return isSameTree(p.left, q.left)&&isSameTree(p.right, q.right);
    }
}
```
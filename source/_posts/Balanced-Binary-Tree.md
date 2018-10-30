---
title: Balanced_Binary_Tree
date: 2016-04-15 12:35:57
categories: [code]
tags: [leetcode,Tree,Depth-first Search]
comments: yes
layout: post
---

## 题目

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

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
    public boolean isBalanced(TreeNode root) {
        return depth(root)!=-1?true:false;
    }
    
    public int depth(TreeNode root) {
        if(null == root)
            return 0;
        int left = depth(root.left);
        if(left == -1)
            return -1;
        int right = depth(root.right);
        if(right == -1)
            return -1;
        if(left - right > 1 || right - left > 1)
            return -1;
        return Math.max(left,right) + 1;
    }
}
```
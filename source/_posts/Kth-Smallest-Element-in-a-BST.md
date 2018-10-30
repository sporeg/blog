---
title: Kth_Smallest_Element_in_a_BST
date: 2016-04-06 11:54:06
categories: [code]
tags: [leetcode,Tree,Binary Search]
comments: yes
layout: post
---

## 题目

Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.

**Note: **

You may assume k is always valid, 1 ≤ k ≤ BST's total elements.

**Follow up:**

What if the BST is modified (insert/delete operations) often and you need to find the kth smallest frequently? How would you optimize the kthSmallest routine?

**Hint:**

> Try to utilize the property of a BST.
> What if you could modify the BST node's structure?
> The optimal runtime complexity is O(height of BST).

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
    public int kthSmallest(TreeNode root, int k) {
        int leftCount = countNode(root.left);
        if(k<=leftCount)
            return kthSmallest(root.left, k);
        else if(k==leftCount+1)
            return root.val;
        else
            return kthSmallest(root.right, k-leftCount-1);
        
    }
    
    private int countNode(TreeNode root){
        if(root==null)
            return 0;
        return 1 + countNode(root.left) + countNode(root.right);
    } 
}
```

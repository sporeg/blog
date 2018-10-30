---
title: Count_Complete_Tree_Nodes
date: 2016-03-29 12:41:39
categories: [code]
tags: [leetcode,Tree,Binary Search]
fullview: 
shortinfo: 
description: 
comments: yes
layout: post
---

## 题目

Given a complete binary tree, count the number of nodes.

Definition of a complete binary tree from Wikipedia:

> In a complete binary tree every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.

## 解题思路

1）BFS

2）DFS

## 代码

BFS	**超时**

``` java
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
    public int countNodes(TreeNode root) {
        if(null==root)
            return 0;
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        int num = 0;
        queue.add(root);
        while(!queue.isEmpty()){
            num++;
            TreeNode checkNode = queue.poll();
            if(null!=checkNode.left){
                queue.add(checkNode.left);
            }
            if(null!=checkNode.right){
                queue.add(checkNode.right);
            }
        }
        return num;
    }
}
```

根据定义改用DFS

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
    public int countNodes(TreeNode root) {
        int leftDepth = countLeftDepth(root);
        int rightDepth = countrightDepth(root);
        
        if(leftDepth == rightDepth)
            return (1 << leftDepth) -1;
        else
            return 1 + countNodes(root.left) + countNodes(root.right);
    }
    
    private int countLeftDepth(TreeNode root){
        int num = 0;
        while(null!=root){
            num++;
            root = root.left;
        }
        return num;
    }
    
    private int countrightDepth(TreeNode root){
        int num = 0;
        while(null!=root){
            num++;
            root = root.right;
        }
        return num;
    }
}
```
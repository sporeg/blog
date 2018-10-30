---
title: Binary_Tree_Level_Order_Traversal
date: 2016-05-10 11:58:26
categories: [code]
tags: [leetcode,Binary Search,Array]
comments: yes
layout: post
---

## 题目

Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example:

Given binary tree {3,9,20,#,#,15,7},

```
    3
   / \
  9  20
    /  \
   15   7
```

return its level order traversal as:

```
[
  [3],
  [9,20],
  [15,7]
]
```

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
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> resultList = new LinkedList<List<Integer>>();
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        if(null == root) 
            return resultList;
        queue.offer(root);
        while(!queue.isEmpty()) {
            int level = queue.size();
            List<Integer> subList = new LinkedList<Integer>();
            for(int i=0; i<level; i++) {
                TreeNode node = queue.poll();
                if(node.left != null) 
                    queue.offer(node.left);
                if(node.right != null) 
                    queue.offer(node.right);
                subList.add(node.val);
            }
            resultList.add(subList);
        }
        return resultList;
    }
}
```
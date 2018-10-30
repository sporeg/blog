---
title: Linked_List_Cycle
date: 2016-04-05 16:30:14
categories: [code]
tags: [leetcode,Linked List,Two Pointers]
comments: yes
layout: post
---

## 题目

Given a linked list, determine if it has a cycle in it.

**Follow up:**

Can you solve it without using extra space?

## 解题思路

> slow = k
> fast = 2k
> 2k-k = nr (n=1)

## 代码

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while(slow!=null && fast!=null){
            slow = slow.next;
            if(fast.next==null)
                return false;
            fast = fast.next.next;
            if(slow==fast)
                return true;
        }
        return false;
        
    }
}
```
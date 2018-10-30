---
title: Linked_List_Cycle_II
date: 2016-04-06 09:38:24
categories: [code]
tags: [leetcode,Linked List,Two Pointers]
comments: yes
layout: post
---

## 题目

Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

Note: Do not modify the linked list.

**Follow up:**

Can you solve it without using extra space?

## 解题思路

> slow = k
> fast = 2k
> 2k-k = nr
> 环起始点s
> 相遇点距环起始点m
> s + m = k = nr
> s = (n-1)r+(r-m) (n=1)

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
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        boolean flag = false;
        while(slow!=null && fast!=null){
            slow = slow.next;
            if(fast.next==null)
                return null;
            fast = fast.next.next;
            if(slow==fast){
                flag = true;
                break;
            }
        }
        if(!flag)
            return null;
        slow = head;
        while(slow!=fast){
            slow = slow.next;
            fast = fast.next;
        }
        return slow;
    }
}
```
---
title: Swap_Nodes_in_Pairs
date: 2016-04-14 11:28:52
categories: [code]
tags: [leetcode,Linked List]
comments: yes
layout: post
---

## 题目

Given a linked list, swap every two adjacent nodes and return its head.

For example,

Given 1->2->3->4, you should return the list as 2->1->4->3.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.

## 代码

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode swapPairs(ListNode head) {
        if(null==head || null==head.next)
            return head;
        ListNode first = head;
        ListNode second = head.next;
        ListNode headNode = second;
        while(null!=first&&null!=second) {
            ListNode nextFirst = second.next;
            if(null == nextFirst || null == nextFirst.next) {
                first.next = nextFirst;
                second.next = first;
                first = nextFirst;
                second = null;
            }else {
                first.next = nextFirst.next;
                second.next = first;
                first = nextFirst;
                second = nextFirst.next;
            }
        }
        return headNode;
    }
}
```
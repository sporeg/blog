---
title: Reverse_Linked_List
date: 2016-03-23 16:04:04
layout: post
categories: [code]
tags: [leetcode,Linked List]
fullview: 
shortinfo: 
description: 
comments: yes
thread: 8
---

## 题目

Reverse a singly linked list.

## 代码

``` c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* reverseList(struct ListNode* head) {
    if(NULL==head)
        return NULL;
    struct ListNode* pnode = head->next;
    struct ListNode* pnext;
    head->next = NULL;

    while(NULL!=pnode)
    {
        pnext = pnode->next;
        pnode->next = head;
        head = pnode;
        pnode = pnext;
    }
    return pnode->next;
}
```
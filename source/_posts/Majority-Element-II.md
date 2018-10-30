---
title: Majority_Element_II
date: 2016-03-31 19:36:42
categories: [code]
tags: [leetcode,Array]
fullview: 
shortinfo: 
description: 
comments: yes
layout: post
---

## 题目

Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times. The algorithm should run in linear time and in O(1) space.

**Hint:**

How many majority elements could it possibly have?

## 解题思路

最多有两个数，分别记录即可

## 代码

```c
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* majorityElement(int* nums, int numsSize, int* returnSize) {
    int mnum1=0,mnum2=1;
    int count1=0,count2=0;
    int i;
    int *returnArray;
    * returnSize = 0;
    for(i=0;i<numsSize;i++){
        if(mnum1==nums[i]){
            count1++;
        }else if(mnum2==nums[i]){
            count2++;
        }else if(count1==0){
            mnum1=nums[i];
            count1=1;
        }else if(count2==0){
            mnum2=nums[i];
            count2=1;
        }else{
            count1--;
            count2--;
        }
    }
    count1=0,count2=0;
    for(i=0;i<numsSize;i++){
        if(mnum1==nums[i]){
            count1++;
        }else if(mnum2==nums[i]){
            count2++;
        }
    }
    if(count1>numsSize/3){
        (*returnSize)++;
    }
    if(count2>numsSize/3){
        (*returnSize)++;
    }
    if(*returnSize==0)
        return NULL;
    returnArray = (int *)malloc(sizeof(int) * (*returnSize));
    i=0;
    if(count1>numsSize/3){
        returnArray[i]=mnum1;
        i++;
    }
    if(count2>numsSize/3){
        returnArray[i]=mnum2;
    }
    return returnArray;
}
```
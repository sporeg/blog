---
title: Bulb_Switcher
date: 2016-04-07 12:31:27
categories: [code]
tags: [leetcode,Math,Brainteaser]
comments: yes
layout: post
---

## 题目

There are n bulbs that are initially off. You first turn on all the bulbs. Then, you turn off every second bulb. On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on). For the ith round, you toggle every i bulb. For the nth round, you only toggle the last bulb. Find how many bulbs are on after n rounds.

**Example:**

> Given n = 3. 
> 
> At first, the three bulbs are [off, off, off].
> After first round, the three bulbs are [on, on, on].
> After second round, the three bulbs are [on, off, on].
> After third round, the three bulbs are [on, off, off]. 
> 
> So you should return 1, because there is only one bulb is on.

## 解题思路

灯泡1-n

以第k个灯泡为例

k在i轮变化,k能被i整除

**如：**

> k = 10
> i=(1,10),(2,5)

> k = 9
> i=(1,9),(3)

所以：当k是平方数时灯泡最终会亮，否则会灭

1个灯泡中有1个平方数

2个灯泡中有1个平方数

3个灯泡中有1个平方数

4个灯泡中有2个平方数

...

n个灯泡中有sqrt(n)个平方数

## 代码

```java
public class Solution {
    public int bulbSwitch(int n) {
        return (int)Math.sqrt(n);
    }
}
```


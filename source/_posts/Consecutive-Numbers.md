---
title: Consecutive_Numbers
date: 2016-04-01 11:51:26
categories: [code]
tags: [leetcode]
comments: yes
layout: post
---

## 题目

Write a SQL query to find all numbers that appear at least three times consecutively.

> +----+-----+
> | Id | Num |
> +----+-----+
> | 1  |  1  |
> | 2  |  1  |
> | 3  |  1  |
> | 4  |  2  |
> | 5  |  1  |
> | 6  |  2  |
> | 7  |  2  |
> +----+-----+

For example, given the above Logs table, 1 is the only number that appears consecutively for at least three times.

## 代码

**超时**

```SQL 
# Write your MySQL query statement below
Select DISTINCT l1.Num from Logs l1, Logs l2, Logs l3 
where l1.Id=l2.Id-1 and l2.Id=l3.Id-1 
and l1.Num=l2.Num and l2.Num=l3.Num
```

```SQL
# Write your MySQL query statement below
select distinct t1.num 
from Logs t1 join Logs t2 on t1.Num = t2.Num 
    join Logs t3 on t1.Num = t3.Num 
where t2.Id - t1.Id = 1 and t3.Id - t2.Id =1; 
```
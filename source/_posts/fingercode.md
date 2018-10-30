---
layout: post
title: FingerCode
date: 2016-03-07
categories: [study]
tags: [fingercode,biometric]
fullview: 
shortinfo: 
description: FingerCode基本流程
comments: yes
thread: 1
---

## 生物识别系统 biometric system

================================================

生物识别系统通过生物信息区分 *被授权者(authorized person)* 与 *伪装者(imposter)*

一般可分为两类： *验证系统(verification mode)* 与 *识别系统(identification mode)*

## FingerCode流程

================================================

最早发表于 *Filterbank-Based Fingerprint Matching* ，主要用于验证系统。

### 处理流程

![FingerCode处理流程][1]

1）找出指纹参考点（会发生偏移）

2）以参考点为圆心，设定半径的圆形区域划分扇区

```
角度划分arcs个，沿径向分bands个，共sectors=arcs*bands个区域
```

3）用一组disk个Gabor滤波器组对指纹图像滤波

4）计算滤波图像中每个扇形区内灰度值对平均值的*平均绝对离差(Average Absolute Deviation)*

```
得到FingerCode为disk*sectors维的向量
```

### 验证流程

对FingerCode进行旋转匹配，即匹配arcs次，比较欧氏距离，小于阈值即验证成功


[1]: /images/fingercode.jpg "System diagram of Fingercode"

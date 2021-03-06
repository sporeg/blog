---
layout: post
title: SSDsim
date: 2016-03-17
categories: [study]
tags: [SSD,SSDsim]
fullview: 
shortinfo: 
description: SSDsim原理及学习笔记
comments: yes
thread: 5
---

## 简介

SSDsim采用事件驱动方法，提供对时间和能耗的模拟

### 作用

*	给研究开发人员提供一个前期功能验证的手段
*	降低开发成本
*	提前验证所设计的硬件结构，软件算法的有效性

### 开源固态盘模拟器

*	[DiskSim](http://www.pdl.cmu.edu/DiskSim/)
*	Flashsim
*	[SSDsim](http://storage.hust.edu.cn/SSDsim/)

### 优势

*	数据缓存区的模拟
*	能耗结果的模拟
*	闪存高级命令的模拟


## 时间模拟

================================================================

| 简称 | 含义 | 时间 |
| --- |:---:|  ---:|
| t(R) | 数据从目标物理页中读到分组的寄存器所消耗的时间 | 20  微秒 |
| t(PROG) | 数据从分组的寄存器写到目标物理页所消耗的时间 | 200 微秒 |
| t(ERASE) | 目标物理块的擦除时间	| 1.5 毫秒 |
| t(WC) | 通过数据总线上向寄存器传输一个字节的数据所消耗的时间 | 25  纳秒 |
| t(RC) | 通过数据总线从寄存器向外传输一个字节的数据所消耗的时间 | 25  纳秒 |
| PS | 传输的数据量 |	

================================================================

### 读

**输入命令地址阶段**

首先花费一个t(WC)时间通过总线传输一个起始命令（00h）

之后花费5个t(WC)时间通过总线传输读操作的地址

紧接着是花费一个t(WC)时间传输结束命令（30h）

**访问介质阶段**

闪存将数据从介质中读到分组的数据寄存器上

**数据传输阶段**

读出的数据从数据寄存器通过总线传输到通道控制器的缓存中

传输时间与传输的数据量(PS)有关

总时间：

```
7×t(WC)+t(R)+PS×t(RC)
```

### 写

**输入命令地址阶段**

首先花费一个t(WC)时间通过总线传输一个起始命令（80h）

之后花费5个t(WC)时间通过总线传输写操作的地址

花费一个t(WC)时间传输结束命令（10h）

**数据传输阶段**

将数据从通道控制器的缓存传输到分组的数据寄存器上

传输时间与传输的数据量(PS)有关

**访问介质阶段**

传入的数据从数据寄存器写到介质中

总时间：

```
7×t(WC)+PS×t(WC)+t(PROG)
```

### 擦除

总时间：

```
5×t(WC)+t(ERASE)
```

### 状态

**通道状态**

==============================================

| 独立服务单元状态 | 含义 | 停留时间 |
|:---:|:---:|:---:|
| CHANNEL_IDLE | 空闲 | (0,∞) |
| CHANNEL_C_A_TRANSFER | 命令地址传输 | 7×t(WC) |
| CHANNEL_DATA_TRANSFER | 数据传输	| PS×t(RC) |

==============================================

**芯片状态**

===========================================

| 独立服务单元状态 | 含义 | 停留时间 |
|:---:|:---:|:---:|
| CHIP_IDLE | 空闲 | (0,∞) |
| CHIP_WRITE_BUSY | 介质操作：写 | t(PROG) |
| CHIP_READ_BUSY | 介质操作：读	| t(R) |
| CHIP_C_A_TRANSFER | 接收命令地址	| 7×t(WC) |
| CHIP_DATA_TRANSFER | 数据传输	| PS×t(RC) |

===========================================

**状态变化图**

![读写状态变化图](/images/ssdsim1.png)

## 能耗模拟

### 处理器

*	不管采用什么样硬件结构和软件算法，处理器的能耗基本相同
*	SSDsim中，不考虑处理器的能耗

### 闪存

*	时间
*	闪存芯片的数据手册给出了在不同状态之间转换时的电流和电压（3.3V）

### DRAM工作状态

*	激活状态（active）
	*	对DRAM进行读写操作
	*	能耗可以根据所使用的内存颗粒的电压电流以及内存操作时间计算获得
*	低功耗状态（standby）
	*	短时间内没有对DRAM进行读写操作
	*	两次读写操作之间的间隔时间
*	刷新状态（refresh）
	*	长时间内没有对DRAM有读写操作
	*	特定DRAM芯片的刷新周期是一定的
	*	根据负载的时间跨度，DRAM的刷新周期，以及DRAM的大小既DRAM刷新单位计算获得
	
## 框架

### 模块

硬件结构	闪存颗粒、固态盘内部通道等

闪存转换层	数据缓存区、地址映射、垃圾回收及损耗均衡等

*	硬件行为层
	ONFI 2.2协议
	*	数据迁移（copy-back）
	*	多分组操作（multi-plane）
		*	多分组读操作（multi-plane read）
		*	多分组写操作（multi-plane write）
		*	多分组擦除操作（multi-plane write）
	*	交错操作（interleave）
*	闪存转换层
	*	地址映射
	*	垃圾回收
	*	损耗均衡
*	数据缓存层
	模拟各种固态盘的数据缓存管理算法

### 代码结构

*	ssd.h/.c
	*	主文件
*	initialize.h/.c
	*	数据结构定义和初始化
*	flash.h/.c
	*	请求执行，缓冲区管理，
	*	模拟SSD硬件读操作、写操作、擦除操作
	*	支持高级命令（多个page读写，提高读写速度）
*	avlTree.h/.c
	*	管理缓冲区，使用AVL平衡树管理
*	pagemap.h/.c
	*	模拟地址转换和擦除，损耗平衡，垃圾回收

### 数据结构

===========================================================================

| 名称 | 模拟对象 | 主要成员 |
|:--- |: --- |:--- |
| ssd_info | 一个固态盘 | channel_head、dram、current_time、request_queue、request_tail、{子请求}、{统计} |
| channel_info | 一个通道 | chip_head、{状态+时间}、{子请求}、{统计} |
| chip_info | 一个芯片 | die_head、{状态+时间}、{统计} |
| die_info | 一个晶圆 | plane_head |
| plane_info | 一个分组 | blk_head、add_reg_ppn、free_page |
| blk_info | 一个物理块 | page_head、erase_count、free_page_num、invalid_page_num、last_write_page |
| page_info | 一个物理页 | valid_state、free_state、lpn |
| dram_info | 固态盘中内存 | map、buffer |
| map_info | 映射关系区域 | {统计}、map_entry |
| buffer_info | 数据缓存区域 | {队列}、{统计}、pTreeHeader |
| buffer_group | 数据缓存节点 | {队列}、group、stored、dirty_clean |
| entry | 映射关系 | Pn、state |

===========================================================================	

### 基本流程

![SSDsim流程图](/images/ssdsim2.png)

initialize: 读入参数，建立与之对应的结构体

pre_process: 预先处理所有的读请求

make_aged: 生成部分保持有失效数据的存储空间，以模拟使用过一段时间的固态盘

当需要访问闪存时，需要执行分布函数，在分布函数中，根据参数文件给出的分布方法参数，将外部请求分散成独立的子请求，挂在相应的通道的子请求队列（sub_request）

### 配置文件 page.parameters

*	硬件组织结构

===========================================================================	

| 参数 | 名称 |
|:---|:---|
|dram capacity		|缓冲区大小|
|channel number	|通道数|
|chip number		|芯片数|
|die number		|晶圆数|
|plane number		|分组数|
|block number		|物理块数|
|page number		|物理页数|
|subpage page		|子页数|
|page capacity		|物理页大小(B)|
|subpage capacity	|子页大小(B)|

===========================================================================	

*	时间参数

| 参数 | 含义 | 时间 |
| --- |:---:|  ---:|
| t(R) | 数据从目标物理页中读到分组的寄存器所消耗的时间 | 20  微秒 |
| t(PROG) | 数据从分组的寄存器写到目标物理页所消耗的时间 | 200 微秒 |
| t(ERASE) | 目标物理块的擦除时间	| 1.5 毫秒 |
| t(WC) | 通过数据总线上向寄存器传输一个字节的数据所消耗的时间 | 25  纳秒 |
| t(RC) | 通过数据总线从寄存器向外传输一个字节的数据所消耗的时间 | 25  纳秒 |
| PS | 传输的数据量 |	|

*	能耗参数

===========================================================================	

| 参数 | 名称 |
|:---|:---|
|flash supply voltage		|闪存工作电压|
|dram cative current		|内存芯片的激活电流|
|dram standly current		|低功耗状态|
|dram refresh current		|刷新状态电流|
|dram voltage			|内存工作电压|

===========================================================================	

*	闪存转换层算法参数
*	数据缓存算法参数

### trace文件 xxx.ascii

记录特定的负载的所有的请求的到达时间，请求的类型，请求的逻辑地址，请求的大小

===========================================================================	

| arrive | dev | lsn | size | ope |
|:---:|:---:|:---:|:---:|:---:|
|0 |0 |303567 |7 |0|
|0 |1 |55590 |6 |0|
|26214000 |0 |303574 |7 |0|
|26214000 |1 |240840 |6 |0|

===========================================================================	

trace文件特点

===========================================================================

| trace | 读请求平均大小(KB) | 写请求平均大小(KB) | 写请求比例 |
|:---:|---:|---:|:---:|
|radius|6.57|7.70|90.93%|
|MSNFS|14.88|10.60|15.45%|
|Financial|2.38|3.84|85.19%|

===========================================================================

其中，写请求比例较大的远程用户拨号认证系统服务器上采集的trace：**RADIUS_SQL.ascii**

### 结果输出 ex.out statistic10.dat

===========================================================================	

| 参数 | 名称 |
|:---|:---|
|read request count			|读请求次数|
|write request count			|写请求次数|
|read request average size		|读请求平均大小|
|write request average size		|写请求平均大小|
|read request average response time	|读请求平均延迟|
|write request average response time	|写请求平均延迟|
|buffer read hits				|读命中|
|buffer read miss				|读miss|
|buffer write hits				|写命中|
|buffer write miss				|写miss|

===========================================================================	

### 操作方法

*	进入ssdsim-linux目录
*	编译代码：gcc -o ssd *.h *.c
	*	生成可执行文件：ssd
*	调用./ssd运行SSDsim
	*	提示输入trace file name:   example.ascii
*	统计结果在文件ex.out 和 statistic10.dat中
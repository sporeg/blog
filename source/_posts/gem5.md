---
layout: post
title: gem5安装
date: 2016-03-11
categories: [study]
tags: [gem5]
fullview: 
shortinfo: 
description: Ubuntu14.04环境下 gem5安装
comments: yes
thread: 2
---

## Ubuntu14.04 gem5安装

================================================

[安装gem5需要的软件清单以及编译流程](http://www.m5sim.org/Compiling_M5 "gem5") 

## 安装过程

================================================

[参考](http://blog.sina.com.cn/s/blog_548b0a230101cagk.html)

### gem5

[gem5](http://repo.gem5.org/)

gem5-stable就可以了

下载完成后解压

### Python

一般都有，查看版本

> python -V

### python-dev

> sudo apt-get install python-dev

### g++

这个好像也有

> sudo apt-get install g++

### scons

> sudo apt-get install scons

安装完成后查看版本

> scons -v

### swig

[swig](http://swig.org/ "swig") 我下的3.0.8

解压后

> ./configure --without-pcre

> make

> sudo make install

安装完成后查看版本

> swig -version

### zlib

[zlib](http://www.zlib.net/ "zlib") 

解压之后的文件夹放到gem5目录下

安装

> ./configure

> sudo make install

### M4

[M4](http://www.gnu.org/software/m4/m4.html)

解压之后的文件夹放到gem5目录下

安装

> ./configure

> sudo make install

### protobuf

[protobuf](https://code.google.com/p/protobuf/) 上不去

备用 [BaiduPan](http://pan.baidu.com/s/1gdLeHur) 密码: s951

### libprotobuf-dev

> sudo apt-get install libprotobuf-dev

### libgoogle-perftools-dev

> sudo apt-get install libgoogle-perftools-dev

### 编译gem5

> scons build/(arch)/gem5.(binary)

如： scons build/X86/gem5.opt

### 测试

```
Hello world!
```

> ./build/X86/gem5.opt ./configs/example/se.py -c tests/test-progs/hello/bin/x86/linux/hello
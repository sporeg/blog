---
title: parsec3.0+ubuntu14.04(未完)
date: 2016-05-11 11:02:19
categories: [study]
tags: [parsec]
comments: yes
layout: post
---

## 编译

可以查看文档或者

```
./bin/parsecmgmt -help
```

看帮助

编译命令如下

```
sudo ./bin/parsecmgmt -a build
```

## 编译错误

**1	OpenSSL 1.0.1e 与 perl 5.18 不兼容**

```
POD document had syntax errors at /usr/bin/pod2man line 71.
make[1]: *** [install_docs] Error 255
```

**解决**

*	使用perl 5.14.2等低版本
*	删除 pod2man 文件

```
sudo rm /usr/bin/pod2man
```

**2	__mbstate_t 重复定义**

```
error: conflicting types for ‘__mbstate_t’
../include/sys/bsd__types.h:105: note: previous declaration of ‘__mbstate_t’ was here
```

具体报错参考[这里](https://lists.cs.princeton.edu/pipermail/parsec-users/2012-November/001474.html)

**解决**

```
vim /parsec-3.0/pkgs/libs/uptcpip/src/include/sys/bsd__types.h
```

注意bsd和types.h之间是两个下划线_ (坑哭我了)

注释掉102-105行

**3 找不到tbb相关文件**

```
Error: 'env version=tbb /usr/bin/make' failed.
```

**解决**

```
sudo apt-get install -y libtbb2 tbb-examples
```

**4 找不到xt、xmu等相关文件**

```
No package 'xt' found
```

**解决**

```
sudo apt-get install libxt-dev
sudo apt-get install libxmu-dev
```

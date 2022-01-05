---
layout: post
title: "resolv.conf 文件格式"
date: 2022-01-04
---

#### 文件内容

resolv.conf 文件有以下几个项目：

1. domain

   主机的域名，默认为 `$HOSTNAME`。

   作用是当查询一个 dot `.` 数量少于 `ndots` （默认为 1）的域名时，`domain` 会自动加到查询域名的后面。

   比如查询 `foo`，实际系统会查询 `foo.domain`。

2. search

   声明多个域名查询，与 `domain` 选项不能同时存在（系统只认后出现的有效）。

3. nameserver

   上游 DNS 服务器地址，比如 `1.1.1.1` 等。

4. options

   其他选项，比如 `ndots` 等。

#### **参考资料**

1. <https://www.ibm.com/docs/en/aix/7.1?topic=formats-resolvconf-file-format-tcpip>

2. <https://unix.stackexchange.com/questions/386919/what-does-search-localdomain-do-in-resolv-conf>

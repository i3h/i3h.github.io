---
layout: post
title: "VMware Teak"
date: 2022-06-18
---

#### 软件版本

VMware Workstation Player 16.2.3

Linux Debian 11 (Host)

Windows 10 (Guest)

#### 问题

1. CPU 100% 占用，虚拟机卡死。

   添加如下内容到 `/etc/sysctl.conf`：

   ```
   # Fix problem where vmware battles with kcompactd0.
   vm.compaction_proactiveness=0
   ```
   
   执行 `sysctl -p` 应用新配置

3. 多核 CPU 设置选项缺失

   在虚拟机文件夹中找到 `.vmx` 文件，添加如下两个选项：
 
   ```
   numvcpus = "8"
   cpuid.coresPerSocket = "4"
   ```
   
   `numvcpu` 为 CPU 逻辑核心总数
 
   `cpuid.coresPerSocket` 为每个 Socket 的核心数
 
   Socket 数量是 `numvcpu / cpuid.coresPerSocket`

#### **参考资料**

1. <https://gist.github.com/2E0PGS/2560d054819843d1e6da76ae57378989?permalink_comment_id=3984605#gistcomment-3984605>

2. <https://communities.vmware.com/t5/VMware-Workstation-Player/Cores-per-Socket-option-not-available-Cores-don-t-show-up/td-p/2873330>

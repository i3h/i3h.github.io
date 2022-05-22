---
layout: post
title: "K8s dnsPolicy"
date: 2022-01-06
---

#### **dnsPolicy 选项**

1. "Default":
   Pod 继承其所在节点的 DNS 配置

2. "ClusterFirst":
   不匹配集群域名后缀的请求会转发至上游 DNS 服务（继承所在节点）

3. "None":
   忽略 K8s 环境，使用 dnsConfig 设置 DNS。

**默认选项是 "ClusterFirst"，而非 "Default"。**

#### **参考资料**

1. <https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/>

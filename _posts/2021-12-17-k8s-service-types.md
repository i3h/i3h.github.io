---
layout: post
title: "K8s Service 类型"
date: 2021-12-17
---

#### **Service 类型**

K8S _Service_ 有几种类型：

1. ClusterIP (default)

   将服务暴露在集群内部

2. NodePort

   将服务暴露在集群外部（ClusterIP Service 会被自动创建）

   可通过 `<NodeIP>:<NodePort>` 访问

3. LoadBalancer

   将服务暴露给云服务的负载均衡（ClusterIP & NodePort Service 会被自动创建）

4. ExternalName

   将服务映射到外部 DNS 记录

#### **参考资料**

1. <https://kubernetes.io/docs/concepts/services-networking/service/>

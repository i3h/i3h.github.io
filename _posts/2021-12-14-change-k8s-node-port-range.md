---
layout: post
title: "修改 K8s Node Port 范围"
date: 2021-12-14
---

#### **修改方法**

在文件 `/etc/kubernetes/manifests/kube-apiserver.yaml` 中加入 `--service-node-port-range=10000-20000`

重启 K8S 服务 `systemctl restart kubelet`

#### **注意事项**

1. 修改 _manifest_ 文件后，_kubelet_ 会无法使用，必须重启一次。

2. _manifests_ 文件夹中的所有文件均视为 _普通文件_，不论文件后缀。所以如果需要进行备份，备份文件必须放到其他地方，否则配置会被覆盖。

#### **参考资料**

1. <http://www.thinkcode.se/blog/2019/02/20/kubernetes-service-node-port-range>

2. <https://github.com/kubernetes/kubernetes/issues/55596>

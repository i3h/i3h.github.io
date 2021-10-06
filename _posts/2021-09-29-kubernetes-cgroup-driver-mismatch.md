---
layout: post
title:  "Kubernetes Cgroup Driver Mismatch"
date:   2021-09-29
---

#### **问题**

kubelet 日志错误信息：

```
misconfiguration: kubelet cgroup driver: \"systemd\" is different from docker cgroup driver: \"cgroupfs\"
```

container runtime 和 kubelet 的 `cgroup driver` 必须保持一致。

kubelet 的 cgroup driver 默认是 `systemd`，而 docker 默认是 `cgroupfs`，这导致 kubelet 一直无法启动。

#### **解决**

修改 `/lib/systemd/system/docker.service`

在 `ExecStart` 后面增加选项 `--exec-opt native.cgroupdriver=systemd`

最后执行 `kubeadm init` 就可以完成 Kubernetes 的初始化。

#### **备注**
完整的 k8s 安装脚本在 GitHub Gist: [init_k8s.sh](https://gist.github.com/i3h/2abf0e4c7d571df7d2649e8b4e15234f)

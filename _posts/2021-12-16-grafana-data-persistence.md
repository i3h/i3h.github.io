---
layout: post
title: "Grafana 数据持久化"
date: 2021-12-16
---

#### **问题**

_kube-prometheus_ 默认提供的 _Grafana_ 数据存储类型为 _emptyDir_，所有数据均会在容器重启后丢失。

#### **数据持久化**

1. 首先创建 PV & PVC 用于存储数据

   ```yaml
   #grafana-volume.yaml
   apiVersion: v1
   kind: PersistentVolume
   metadata:
     name: grafana
   spec:
     capacity:
       storage: 1Gi
     accessModes:
       - ReadWriteMany
     nfs:
       path: "/mnt/data/grafana"
       server: 1.2.3.4
   ---
   apiVersion: v1
   kind: PersistentVolumeClaim
   metadata:
     name: grafana
     namespace: monitoring
   spec:
     accessModes:
       - ReadWriteMany
     resources:
       requests:
         storage: 1Gi
   ```

2. 修改 _kube-prometheus/manifests/grafana-deployment.yaml_

   将 _emptyDir_ 改为创建的 PVC

   ```yaml
   - name: grafana-storage
     persistentVolumeClaim:
       claimName: grafana
   ```

#### **初始密码**

在 _kube-prometheus/manifests/grafana-deployment.yaml_ 中添加 _env_，可以修改默认的初始密码（admin:admin）。

```yaml
env:
  - name: GF_SECURITY_ADMIN_USER
    value: admin
  - name: GF_SECURITY_ADMIN_PASSWORD
    value: password
```

#### **其他问题**

如果在一个浏览器中创建了 Dashboard，然后再从其他浏览器访问时会不显示新创建的 Dashboard，需要搜索一次才会显示在首页上。

#### **参考资料**

1. <https://finolo.gy/2020/03/Grafana%E5%AE%89%E8%A3%85%E5%8F%8A%E6%8C%81%E4%B9%85%E5%8C%96/>

2. <https://www.reddit.com/r/grafana/comments/fuq2qi/grafana_dashboards_not_shown_when_accessing_from/>

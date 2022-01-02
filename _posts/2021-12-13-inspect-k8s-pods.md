---
layout: post
title: "检查 K8s Pod"
date: 2021-12-13
---

#### **SSH K8S Pods 命令**

```sh
k exec --stdin --tty <pod-name> -- /bin/bash
```

#### **Double Dash**

_Double Dash_ 之后的参数不作为 _option_，而视为 _positional parameter_。

```sh
grep -- --hello data.txt
```

上述命令中，_grep_ 将匹配 _--hello_，而不是将其作为 _option_。

#### **Single Dash**

```sh
curl -sL https://rpm.nodesource.com/setup_6.x | sudo -E bash -
```

_bash_ 末尾的 Dash 会让 _bash_ 读取 _stdin_，即前面 _curl_ 的输出内容。

#### **参考资料**

1. <https://www.codegrepper.com/code-examples/shell/kubectl+ssh+into+pod>

2. <https://www.baeldung.com/linux/double-dash-in-shell-commands>

3. <https://superuser.com/questions/1388584/what-does-the-last-hyphen-mean-in-options-of-bash>

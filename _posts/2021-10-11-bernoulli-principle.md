---
layout: post
title: "伯努利方程"
date: 2021-10-11 21:53
---

#### **基本概念**

$$
\frac{1}{2}\rho v^2 + \rho gh + p = const
$$

#### **证明过程**

![BernoullisLawDerivationDiagram.svg](/assets/BernoullisLawDerivationDiagram.svg)

做功能量、动能变化、势能变化分别为：

$$
\begin{aligned}
&\Delta E_w = p_1A_1v_1\Delta t - p_2A_2v_2\Delta t\\
~\\
&\Delta E_k = \frac{1}{2}\rho A_1v_1\Delta tv_1^2 - \frac{1}{2}\rho A_2v_2\Delta tv_2^2\\
~\\
&\Delta E_g = \rho A_1v_1\Delta tgh_1 - \rho A_2v_2\Delta tgh_2
\end{aligned}
$$

能量守恒：

$$
\Delta E_w + \Delta E_k + \Delta E_g = 0
$$

假设流体不可压缩：

$$
A_1v_1 = A_2v_2 = const
$$

带入可得：

$$
\frac{1}{2}\rho v_1^2 + \rho gh_1 + p_1 = \frac{1}{2}\rho v_2^2 + \rho gh_2 + p_2
$$

#### **参考资料**

1. <https://en.wikipedia.org/wiki/Bernoulli%27s_principle>

2. <https://zh.wikipedia.org/wiki/%E4%BC%AF%E5%8A%AA%E5%88%A9%E5%AE%9A%E5%BE%8B>

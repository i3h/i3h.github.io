---
layout: post
title: "信任链"
date: 2021-10-07
---

#### **信任链**

前文 [Digital Certificate](/digital-certificate) 说明了如何解决发信人身份认证的问题。

其根源在于任何加密方法都需要一次分发密钥的过程，这个分发过程的安全性决定了之后的通信安全。

CA 的 Root Certificate 内置于操作系统，相当于第一次分发。之后的信息认证、密钥分发等操作都依赖于第一次分发，所以第一次安全即可认为第二次安全、第三次安全，以此类推。**这就是一条信任链**。

#### **中间证书**

在实际情况中，CA 不会直接使用 Root Private Key 为用户签发证书。因为一旦 Root Private Key 泄露，所有人都必须将对应的 Root Certificate 从系统中移除，这个操作成本很大、涉及面很广。

CA 会签发多个 Intermediate Certificate 用于为用户签发 End Entity Certificate。如果中间证书的私钥泄露，CA 可以吊销相关证书，影响范围会小很多。

![chain_of_trust](/assets/Chain_Of_Trust.svg)

#### **参考资料**

1. <https://en.wikipedia.org/wiki/Chain_of_trust>

2. <https://en.wikipedia.org/wiki/Public_key_certificate>

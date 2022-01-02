---
layout: post
title: "电子签名"
date: 2021-10-05
---

#### **密钥对**

非对称加密算法（Asymmetric Cryptography）可以生成密钥对（key pairs），它的特性是：

- 信息用 Key A 加密后只能被 Key B 解密，反之亦然。

- 两个 Key 分别作为公钥（Public Key）和私钥（Private Key），私钥不能泄漏，而公钥可公开分发。

#### **签名过程**

1. 文本通过 Hash 输出摘要(Message Digest)

   ![generate_hash](/assets/generate_hash.png)

2. 摘要通过私钥加密输出签名(Signature)

   ![generate_signature](/assets/generate_signature.png)

3. 签名附加到文本之后

   ![append_signature](/assets/append_signature.png)

4. 收信人对比两个摘要

   - Hash 文本

   - 用公钥解密签名

   这两个结果应该是一致的，否则说明文本被篡改。

   ![compare_hash](/assets/compare_hash.png)

#### **参考资料**

1. <https://ssd.eff.org/en/module/deep-dive-end-end-encryption-how-do-public-key-encryption-systems-work>

2. <http://www.youdzone.com/signature.html>

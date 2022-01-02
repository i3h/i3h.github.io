---
layout: post
title: "电子证书"
date: 2021-10-06
---

#### **前言**

[Digital Signature](/digital-signature) 可以防止数据被篡改，但无法解决发信人的身份认证问题。

任何人都可以分发给别人一个公钥，并声称自己代表某人。

解决这个问题的方法是由 [Certificate Authority](https://en.wikipedia.org/wiki/Certificate_authority) (CA) 签发证书。

#### **证书内容**

签发 Certificate 需要以下内容：

- 申请者的信息（如名字）

- 申请者的公钥

CA 用自己的私钥对上述信息进行签名，即得到了 Certificate。

![PublicKeyCertificateDiagram_It.svg](/assets/PublicKeyCertificateDiagram_It.svg)

#### **验证过程**

发信人将加密数据和证书一并发给收信人，收信人可通过以下过程验证来信内容及发信人身份：

1. 根据证书里的 CA 信息，使用对应 CA 的公钥验证证书的签名及内容。

2. 证书里包含了发信人的身份信息和公钥，使用发信人的公钥解密收到的加密数据。

**CA 的公钥是内置于系统或浏览器中的**

#### **参考资料**

1. <https://en.wikipedia.org/wiki/Public_key_certificate>

2. <http://www.youdzone.com/signature.html>

---
layout: post
title: "证书撤销"
date: 2021-10-07 13:09
---

#### **撤销证书方法**

当某个中间证书私钥泄露，CA 需要撤销证书以防止出现证书伪造。

用户检验证书是否被撤销有两种方式：

- Certificate Revocation List (CRL)

- Online Certificate Status Protocol (OCSP)

#### **CRL**

CRL 是由 CA 发布的撤销证书列表，用户可以下载列表，并进行查找对比。

CRL 的缺陷是定期更新时间间隔较长；而且列表文件太大，每次验证都要下载和查表的开销太大。

#### **OCSP**

OCSP 是由 CA 提供的在线服务，用户可以一次只请求验证一个证书信息。

OCSP 的缺陷是：

1. 隐私泄露

   由于用户每次都会将特定证书信息发给 CA，所以 CA 会知道用户访问了哪个网站，或者用户在使用什么软件。

   苹果 OCSP 事件：

   <https://blog.jacopo.io/en/post/apple-ocsp/>

   <https://www.macrumors.com/2020/11/15/apple-privacy-macos-app-authenticaion/>

2. 网络不稳定

   如果用户因网络不稳定，或者 CA 的 OCSP 服务器出现故障，导致请求验证失败，客户端有两种选择：

   - Hard Fail

     认为证书无效，禁止访问。

   - Soft Fail

     认为证书有效，允许访问。

   这种情况下，用户可能会出现打开网页显示空白页，需要等待一段时间才能访问网页。

   Let's Encrypt 事件：

   OCSP 服务器 `ocsp.int-x3.letsencrypt.org` 被墙，导致国内用户访问使用了 LE 证书的网站非常缓慢。

#### **OCSP Stapling**

网站提供者可以自己访问 OCSP 服务请求验证，并将验证结果一同发给用户。这样用户就不需要再和 OCSP 服务通信，节省了连接时间，也避免了连接失败的情况。

OCSP 的验证结果包含 CA 的签名，所以网站提供者无法伪造。

#### **参考资料**

1. <https://en.wikipedia.org/wiki/Certificate_revocation_list>

2. <https://en.wikipedia.org/wiki/Online_Certificate_Status_Protocol>

3. <https://www.appviewx.com/education-center/what-is-certificate-revocation-and-when-should-i-do-it/>

4. <http://ijecorp.blogspot.com/2016/01/ocsp-crl.html>

5. <https://blog.jacopo.io/en/post/apple-ocsp/>

6. <https://www.macrumors.com/2020/11/15/apple-privacy-macos-app-authenticaion/>

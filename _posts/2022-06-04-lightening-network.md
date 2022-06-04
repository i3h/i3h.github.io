---
layout: post
title: "Lightening Network"
date: 2022-06-04
---

#### **概念**

闪电网络是基于比特币网络的 _Layer 2 支付协议_

Payer 先在闪电网络中存入一定数量 Bitcoin，之后可以与 Payee 打开双向通道。

两者之间可以进行多次支付记账，但这些信息不直接写入比特币主链。

当双方交易结束后可以关系支付通道，并将记账结果写入主链。

在此过程中一共只有开通和关闭两次写入过程，大大减少了主链记录数量。

#### **特点**

闪电网络的支付通道类似洋葱网络，交易者之间不必直接开通通道，只要两者中间存在中继，即可完成支付。

#### **参考资料**

1. <https://en.wikipedia.org/wiki/Lightning_Network>

2. <https://www.investopedia.com/tech/bitcoin-lightning-network-problems/>

3. <https://lightning.network/>
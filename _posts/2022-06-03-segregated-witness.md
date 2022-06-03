---
layout: post
title: "Segregated Witness"
date: 2022-06-03 22:42
---

#### **基本概念**

Segregated Witness (SegWit) 是比特币网络的一个改进方案，可以增加区块数据容量、提高交易速度。

#### **问题**

Bitcoin 每个区块大小限制为 1MB，并且平均每个区块产生速度约为 10min。因此比特币网络的交易速度被限制为大约 3- 7 Tx/s。

#### **SegWit 方案**

区块中的 Signature 被分离出来放在最后，且这部分数据大小只记为实际的 1/4。

新的计量单位称为 Weight Unit (WU)，新方案中区块的大小限制为 4 billion WU, 即 4MB。

#### **参考资料**

1. <https://river.com/learn/terms/s/segwit/>

2. <https://en.bitcoin.it/wiki/Segregated_Witness>

3. <https://bitcoincore.org/en/2016/10/27/segwit-upgrade-guide/>

4. <https://en.wikipedia.org/wiki/SegWit>
---
layout: post
title: "Keynote of Bitcoin White Paper"
date: 2022-06-03
---

#### **Transactions**

![bitcoin-transaction.png](/assets/bitcoin-transaction.png)

比特币的交易过程：

1. Payer:

   _**Sign**_ ( _**Hash**_ ( Last Transaction Data + Payee's Public Key ) )

2. Payee:
   
   Verify with payer's public key

#### **Proof-of-Work**

![proof-of-work](/assets/proof-of-work.png)

每个 Block 包含：

1. 上一个 Block Hash
2. 随机数 Nonce
3. Tx 记录

Proof-of-Work 机制要求 Block Hash 开头的数个 bit 为零。

矿工需要不断尝试 Nonce，直到找到符合要求的随机数，并将结果广播。

#### **比特币网络**

比特币网络工作流程：
1. 新的 Tx 广播至所有节点
2. 每个节点收集 Tx 合并到一个 Block
3. 每个节点计算 Nonce
4. 找到符合要求的 Nonce 后将此 Block 广播至所有节点
5. 其他节点收到新 Block 后对其进行校验
6. 如果其他节点确认接受新的 Block，则会在其基础上计算后续的 Block。

问题：

由于网络送达率不会达到 100%，在上述流程中一定会出现：
1. 网络中同时存在多个不同版本的区块链
2. 新的 Tx 无法送达所有节点

解决方法：

比特币节点认定最长链为有效，如果发现网络中存在比自己正在计算的链更长的版本，则会切换过去。

#### **Merkle Tree & SPV**

![bitcoin-merkle-tree](/assets/bitcoin-merkle-tree.png)

![bitcoin-merkle-tree](/assets/bitcoin-spv.png)

比特币网络节点可以利用 Merkle Tree 减少存储空间并对 Tx 进行验证

Thin Client 只需保存 Block Header，验证 Tx 时获取所需的 Sibling Node Hash 即可完成校验。

#### **Combining & Splitting**

![bitcoin-combining-splitting](/assets/bitcoin-combining-splitting.png)

Transaction 中可以包含多个 Inputs 和 至多 两个 Outputs

一个 Output 支付给 Payee，另一个找零给 Payer。

#### **Privacy**

比特币使用两种方式降低用户被追踪的可能性：
1. 使用经过 Hash 之后的 Public Key 作为地址
2. 每个 Tx 都使用新的 Key Pair

#### **参考资料**

1. <https://bitcoin.org/bitcoin.pdf>

2. <https://en.wikipedia.org/wiki/Proof_of_work>

3. <https://en.wikipedia.org/wiki/Merkle_tree>
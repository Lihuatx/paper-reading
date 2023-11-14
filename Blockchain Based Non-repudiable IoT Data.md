# Blockchain Based Non-repudiable IoT Data

## Summary

*做完笔记最后填写*

## Research Objective

使用区块链技术解决物联网数据交易中存在的信任缺乏的问题

## Problem Statement

> the traditional centralized data sharing/trading mechanism lacks trust guarantee and cannot satisfy the real-time requirement.
>
> 传统的中心化数据共享/交易机制缺乏信任保障，无法满足实时性要求。

解决在物联网数据交易中的由于传统中心化交易方案所存在的信任缺乏问题。

## Method(s)

* 提出了一种**基于区块链的物联网数据交易的不可否认方案**，以解决可信性和实时性限制。拟议的方案有两部分，即**交易方案和仲裁方案**。该交易方案采用分而治之的方法和两种承诺方法来支持高效的物联网数据交易，该交易以两轮方式运行。该仲裁方案首先利用智能合约在链上实时解决纠纷。当链上仲裁不满意时，仲裁方案还采用线下仲裁的方式做出最终解决。

* 所提出的方案使用**智能合约**来支持自动物联网数据交易并实现自动支付。为了实现不可否认性，所提出的方案在区块链上记录数据发送和相应的接收证明。当发生争议时，触发智能合约，利用之前记录的证据实现自动仲裁。

## Evaluation



## Conclusion

## Notes

使用同态哈希和SHA-256的不同主要是同态哈希可以支持在哈希值上进行操作，比如
$$
h(br + bs) = h(br) × h(bs)\, mod \,p
$$
在该论文中提出了使用SHA-256和异或操作来代替同态哈希的哈希值相乘操作
$$
Tag(S) = Hash(S1)⊕Hash(S2)
$$

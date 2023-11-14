## Blockchain-Based Secure Deduplication and Shared Auditing in Decentralized Storage

## Summary

这篇文章所提出的基于区块链的安全数据去重和数据完整性审计方案中，区块链的主要作用是作为公开的分布式账本，记录各种交互和审计过程中产生的记录，用于后续的验证和防止重复审计等。

* 功能性，本方案能够实现安全的数据去重和数据完整性审计两个基本功能。
* 安全，(1)数据保密性是指该方案应保证不同类型数据的数据保密性。 (2)审计结果的可靠性是指在真实密文丢失的情况下，SSP无法通过伪造密文及其相应的认证标签来欺骗审计者。(3)DFA的抵抗性意味着该方案可以保护后续上传者在DFA下不会丢失数据。
* 方便，审计过程可以由两个SSP之间互相进行，不需要TPA或者用户参与。



[1]张桂鹏. 基于区块链的云数据安全存储技术研究[D].广东工业大学,2022.DOI:10.27029/d.cnki.ggdgu.2022.000021.

上面这篇文章中加入了身份认证技术，生成的角色密钥可以在加密过程中实现不同身份的访问限定。

同时提出了密钥安全管理方案。

> 同时提出了一种基于区块链的医疗大数据安全存储方案，以此实现医疗场景下的患者电子医疗记录的安全性、机密性及完整性。为了确保患者电子医疗记录的安全性，该方案利用基于BLS签名技术来为患者电子医疗记录生成医疗防篡改记录，并将该防篡改记录整合成区块链上所部署的交易中，使得验证者都能够在不得悉电子医疗记录的内容下来验证医疗防篡改记录的正确性。此外，患者与医疗机构需要共同执行密钥协商协议来确保加密密钥的安全性，通过该协议，患者可以对电子医疗记录进行加密，并将密文上传到云存储服务器中。同时，该方案支持公平交易机制，即患者和医疗机构能够区块链上部署的智能合约来执行公平可靠的支付协议。安全性分析表明所提方案能够抵抗敌手发起的共谋攻击、篡改攻击和中间人攻击。

## Research Objective

 设计并提出一个基于区块链的去中心化存储方案，以实现安全的重复数据删除和共享审计功能

## Problem Statement

* 现有的云存储服务提供商中存在大量用户上传的重复数据，几乎百分之75都是重复副本数据。
* 为了节省空间人们提出了一些算法来实现加密重复数据删除，这些方案仍然容易受到单点故障（SPOF）的影响，因为每个数据仅存储一份副本在存储服务器中。同样，恶意用户还可以发起重复伪造攻击（DFA）来破坏外包数据的唯一副本。
* 另一方面，用户将数据外包后将失去对其数据的物理控制，这意味着SSP可能会篡改或删除很少访问的数据以节省存储空间。
* 需要保证只有数据所有者才可以访问他们所存放的数据的原数据其他人或者SSP都不能访问存储数据的元数据
* 大多数现有的对于数据完整性的公共审计方案都是不切实际的，因为它们将所有用户的审计任务委托给完全可信的第三方审计员（TPA），而这在应用程序中很难找到。

## Method(s)

* 加密和签名：该系统采用安全哈希加密以及BLS签名协议和区块链技术，以确保数据在上传之前进行加密，并且加密密钥得到安全管理，而不会在链上公开。
* 借助区块链，所提出的方案实现了更有效的空间节省和全局资源优化，从而将存储服务费用降低到数据用户可以接受的程度。在此基础上，我们方案的双服务器存储模型在避免单点故障方面比以往的解决方案更加可行。
* 首先，所提出的重复数据删除协议要求SSP使用两个标签来存储每个数据，其中一个来自明文，另一个来自密文。由于SSP可以验证数据与其第二标签之间的一致性，因此恶意用户发起的DFA将失效。其次，该方案实现了基于区块链的分片审计，使得同一数据的数据用户之间审计认证器和结果可验证地共享。这样，数据使用者就可以随时从区块链上获取外包数据的完整性信息。最后，通过 HCE2 的标签检查，如果用户不信任区块链上发布的审计结果，该方案允许用户在数据检索期间检查数据完整性。
* 所提出的方案利用审计验证器在后续上传阶段实现 PoW。通过使用随机挑战模型，我们的方案确保了所有权挑战随机数的新鲜度，从而使潜在的 PRA 无效。同时，恶意对手无法从窃听的“挑战-响应”实例中获取任何有用的信息来伪造有效的证据。此外，所提出的方案要求审计员通过定期与有效数据用户执行交互协议来更新审计验证器，这使得对手更难发起证明重放攻击。
* 得益于底层 MLE ( HCE2 ) 加密方案 [5]，所提出的方案为外包数据提供了 PRV $ -CDA 级别的安全性，正如 Bellare 等人在 [5] 中所声称的那样。由于 HCE2 算法可以保证两个不可预测消息的密文之间的不可区分性，因此所提出的方案不仅可以防止SSP，而且可以防止恶意对手检索明文，即使他们非法获得了加密数据。

Initial Upload 

~~User选择一个SSP上传文件F，也就是说后面的数据完整性审计的时候是不需要审计员（另一个SSP）拥有完整的F，只需要在区块链上得到验证器σ~~

User要选择两个SSP

## Evaluation

$$
\begin{equation*} \left\lbrace \begin{array}{ll}k_i &=H_1(m_i)\\ c_i &={\mathsf {HCE2.Enc}}(k_i,m_i)\\ T_i &=H_1(c_i)\\ M_i &=H_2(t \parallel i)\\ \sigma _i &=({M_i}u^{T_i})^{sk} \end{array} \qquad 1\leq i \leq n \right.. \tag{1} \end{equation*}
$$



## Conclusion

## Notes

> 在您提到的第 2.3 节中，该段落描述了一个安全游戏，它是正式安全证明的一部分。**该游戏的目的是对对手（表示为 A）和挑战者（表示为 C）之间的交互进行建模，以尝试分析系统内文件密钥对和加密块的安全性。**以下是挑战中每个步骤的作用：
>
>  初始化：挑战者 C 通过创建随机文件并生成必要的加密参数（例如文件密钥对和加密块）来设置场景。除密钥外，这些参数均与对手 A 共享，模拟了对手知道系统公共参数但不知道私钥的真实场景。 
>
> 查询：允许对手 A查询附加信息，这代表攻击的信息收集阶段。对手尝试通过向挑战者查询某些区块的哈希值和签名来尽可能多地了解信息。 
>
> 挑战：挑战者 C 使用 A 尚未查询的区块向 A 提出挑战。此步骤测试对手是否可以使用收集到的信息来成功进行攻击，在本例中，为挑战块生成有效的聚合签名和证明。 
>
> 验证：最后，挑战者 C 验证对手的响应。如果 A 的反应与证明一致，则 A 被认为“赢得”了比赛。这意味着系统存在潜在的弱点。如果 A 未能产生有效的响应，则系统被认为可以安全地抵御此游戏所模拟的攻击。
>
> 此结构旨在模仿对手尝试破坏系统的行为，并表明即使具有一定的知识和能力，对手无法伪造有效签名或以其他方式危及系统的安全。通过这个假设的挑战和验证过程，本文的作者旨在证明他们的系统可以抵御此类攻击，从而证明其安全特性。



![image-20231031202210511](C:\Users\huawei\AppData\Roaming\Typora\typora-user-images\image-20231031202210511.png)

**Here is the detailed explanation for each parameter in the set Para={G1,G2,e,p,g,u,H1,H2,π1,π2}:**

> **G1 and G2:** These are two multiplicative cyclic groups of order p. They are chosen to facilitate the construction of a bilinear map. The selection of these groups is critical for ensuring the security and efficiency of the cryptographic operations within the system.
>
> **e:** This is the bilinear map that takes two elements from G1 and maps them to G2. The bilinear map e is a core component in pairing-based cryptography, which allows for certain complex cryptographic schemes to be built, especially those related to identity-based encryption and attribute-based encryption.
>
> **p:** The order of the groups G1 and G2, which is a large prime number. The size of p is related to the security level of the system, as it determines the difficulty of solving discrete logarithm problems in these groups.
>
> **g:** A generator of G1. It is the basis for generating public keys and other cryptographic operations. A generator is an element from which every other element of the group can be derived.
>
> **u:** A random element selected from G1, used in cryptographic operations to provide randomness and enhance security.
>
> **H1 and H2:** **These are hash functions that map a binary string to an element in Z*_p (the multiplicative group of integers modulo p) and G1, respectively. Hash functions in cryptographic systems are used to ensure data integrity and map data of arbitrary size to data of fixed size.**
>
> **π1 and π2:** Pseudo-random functions that map an integer and an element of Z_p to another element of Z_p. Pseudo-random functions are essential in cryptographic protocols to simulate randomness and are often used to generate keys or challenges in security proofs.
>
> These parameters together define the system's cryptographic primitives and are fundamental to its operation. They are carefully selected and published to enable secure, efficient, and verifiable interactions between the users and the storage service provider, as well as to support the security proofs that underlie the proposed scheme. The parameters are also published on the blockchain to ensure transparency and immutability.”

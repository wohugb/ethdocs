# 算法

我们的算法[Ethash](https://github.com/ethereum/wiki/wiki/Ethash)(以前称为Dagger-Hashimoto)是基于提供一个大型的，瞬态的，随机生成的数据集，它形成了一个DAG ,(Dagger部分)，并试图解决一个特定的约束，部分通过块的头部散列来确定。

它被设计用来在一个缓慢的CPU专用环境中加快验证时间，但是当提供高带宽的大容量内存时，为挖掘提供了巨大的提速。
大的记忆要求意味着大型矿工获得比较小的超线性收益。
高带宽要求意味着在共享相同存储器的许多超高速处理单元上堆积的加速相对于单个单元几乎没有好处。
这一点很重要，因为池开采对节点进行验证没有任何好处，因此阻碍了集中化。

外部挖掘应用程序和以太坊守护进程之间的通信通过JSON-RPC API进行。
提供了两个RPC函数。 ,`eth_getWork`和`eth_submitWork`。

这些在[矿工](https://github.com/ethereum/go-ethereum/wiki/JavaScript-Console#miner)页下的[JSON-RPC接口](https://github.com/ethereum/wiki/wiki/JSON-RPC)维基文章中有正式记录。

为了可以挖掘，您需要一个完全同步的以太坊客户端，该客户端已启用挖矿和至少拥有一个以太坊账户。
这个帐户用于发送挖矿奖励，通常被称为*coinbase*或*etherbase*。
请访问本指南的[创建账号](http://www.ethdocs.org/en/latest/account-management.html#creating-an-account)部分，了解如何创建帐户。

!!! warning "Warning"

    确保您的区块链在开始挖掘之前与主链完全同步，否则您将不会在主链上挖掘。

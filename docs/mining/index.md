# 挖矿简介

挖掘这个词源于加密货币的黄金比喻。
黄金或贵金属稀缺，数字令牌也是如此，增加总量的唯一途径是采矿。
这在以太坊上也是适用的，发布后唯一的发行模式是通过采矿。
与这些例子不同的是，挖矿也是通过在区块链中创建、验证、发布和传播区块来保护网络的方法。

- 挖掘以太币 = 保护网络 = 验证计算

## 什么是挖矿？

以太坊和所有区块链技术一样，采用激励驱动的安全模式。
共识是基于选择总难度最高的区块。
矿工生产其他人检查有效性的块。
在其他格式良好的标准中， 一个块只有在包含给定*难度*的工作证明*(PoW)的情况下才是有效的。
请注意，在以太坊宁静的里程碑， 这很可能会被一个 (查看[权益证明模型](http://www.ethdocs.org/en/latest/mining.html#pos-vs-pow)).

以太坊区块链在很多方面与比特币区块链相似，不过它确实有一些区别。
以太坊和比特币在区块链架构方面的主要区别在于， 不像比特币,以太坊块包含事务列表和最近状态的副本 (merkle patricia trie编码状态的根散列更加精确).
除此之外, 另外两个值, 块号和难度, 也存储在块中.

使用的工作证明算法被称为[Ethash](https://github.com/ethereum/wiki/wiki/Ethash)([Dagger-Hashimoto算法](https://github.com/ethereum/wiki/wiki/Dagger-Hashimoto)的修改版本)并且涉及找到一个*nonce*输入给算法，以便结果低于一定的难度阈值。
PoW算法的要点在于没有更好的策略去寻找这样的随机数，而不是列举可能性，而验证解决方案是微不足道的。
由于输出具有均匀分布(因为它们是应用散列函数的结果),我们可以保证,关闭,找到这种随机数所需的时间取决于难度阈值.
这样就可以通过操作难度来控制查找新块的时间。

按照协议规定, 难度动态地调整，平均每隔15秒由整个网络产生一个块.
我们说网络产生一个* 15秒的块时间*的区块链。
这种“心跳”基本上是对系统状态的同步加以标记，并且保证：除非攻击者拥有超过一半的网络挖掘能力，否则不可能维持分叉(以允许双重花费)或者恶意行为者重写历史记录(这就是所谓的* ,51％攻击*)。

参与网络的任何节点都可以是矿工，他们预期的开采收入将与他们的(相对)采矿能力或者*哈希率*成正比，即每秒由网络的总散列率标准化的随机数。

Ethash PoW *内存硬*，使其* ASIC耐*。
记忆硬度是通过工作证明算法实现的，该算法要求根据随机数选择固定资源的子集
这个资源(几个GB大小的数据)被称为** DAG **。
每个30000块的[DAG](https://github.com/ethereum/wiki/wiki/Ethash-DAG)是完全不同的，这个125小时的窗口被称为* epoch *(大概为5.2天)，需要一段时间才能生成,。
由于DAG只取决于块的高度，所以可以预生成，但如果不是，客户端需要等到这个过程结束才产生一个块。
如果客户端没有提前预生成和缓存DAG，则网络在每个历元转换中可能经历大量的块延迟。
请注意，DAG不需要生成用于验证PoW，实质上允许使用低CPU和小内存进行验证。

作为特殊情况，当您从头开始创建节点时，只有在为当前时期构建DAG后才会开始挖掘。

## 挖掘奖励

获胜块的成功PoW矿工将收到：

- “获胜”区块的静态区块奖励，包含5.0个以太网币
- 燃料消耗的成本 - 依赖于当前燃料价格的以太币量
- 作为块的一部分包括叔叔的额外奖励, 包括每名叔叔额外1/32的形式

由获奖矿工提交的区块内所有交易执行所消耗的所有燃料由每笔交易的发件人支付。
所产生的燃料成本作为共识协议的一部分记入矿工账户。
随着时间的推移，预计这些将会使静态区块奖励变得更加渺小。

*叔叔*是陈旧的块，即父母是包括块的祖先（最多6块）。
为了抵消网络滞后对采矿奖励分散的影响，奖励有效的叔叔, 从而增加安全性 (这被称为GHOST协议).
被成功的PoW矿工组成的街区中的叔叔获得7/8的静态区块奖励（= 4.375以太）。
每个块最多允许2个叔叔。

> - [在reddit上的叔叔ELI5](https://www.reddit.com/r/ethereum/comments/3c9jbf/wtf_are_uncles_and_why_do_they_matter/)
> - [论坛线程解释叔叔](https://forum.ethereum.org/discussion/2262/eli5-whats-an-uncle-in-ethereum-mining)

采矿成功取决于设定的块难度.
块难度动态调整每个块，以调节网络哈希功率产生一个12秒的阻塞时间
因此，找到一个块的机会是相对于哈希率难度而言的。

## Ethash DAG

Ethash使用*DAG*(有向无环图)作为工作证明算法, 这是为每个*epoch*生成的, 也就是说，, 每30000块 (125小时，约5.2天)
DAG需要很长时间才能生成如果客户端只根据需要生成它，则在发现新时代的第一个块之前，您可能会在每个时代转换中看到很长的等待时间。
然而，DAG只取决于块号，因此可以并且应该提前计算以避免在每个历元转换处的漫长的等待时间`geth`和`ethminer`实现自动DAG生成，并且一次维持两个DAG,时代转折
当从控制台控制采矿时，自动DAG生成被打开和关闭
如果使用`--mine`选项启动`geth`，默认情况下也会打开。请注意，客户端共享一个DAG资源，所以如果您正在运行任何客户端的多个实例，请确保在所有客户端中关闭自动DAG生成,但是有一个例子。

为仲裁者生成DAG

```bash
geth makedag <block number> <outputdir>
```

例如`geth makedag 360000〜/ .ethash`请注意，ethash为DAG使用`〜/ .ethash`(Mac / Linux)或`〜/ AppData / Ethash`(Windows)，以便它可以在不同的客户端实现之间共享,以及多个正在运行的实例。
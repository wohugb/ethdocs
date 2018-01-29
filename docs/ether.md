# 以太币

## 什么是以太币？

以太币是以太坊内使用的货币的名称。 它用于支付EVM内的计算. 这是通过购买燃料中的以太币燃料间接完成的.

## 计价

以太坊有一个公制的面额用作以太单位。
每种面额都有自己独特的名字（一些承载着计算机科学和隐秘经济学演变中的重要人物的姓氏）。
以太币的最小面额aka*基本单位*叫魏。
下面是Wei列举的名称及其价值。
遵循一个共同的（虽然有点模棱两可）模式, 以太币也指定一个货币单位 (1e18或者一个奎因).
请注意，这个货币并不像许多人以为的那样被称为以太坊，以太坊也不是一个单位。

|单元                   |wei 值   |wei|
|----------------------|---------|-------------------------|
|**wei**               |1 wei    |1|
|**Kwei (babbage)**    |1e3 wei  |1,000|
|**Mwei (lovelace)**   |1e6 wei  |1,000,000|
|**Gwei (shannon)**    |1e9 wei  |1,000,000,000|
|**microether (szabo)**|1e12 wei |1,000,000,000,000|
|**milliether (finney)** |1e15 wei |1,000,000,000,000,000|
|**ether**             |1e18 wei |1,000,000,000,000,000,000|

关于以太币单位的人名解释，请查看[知乎页面](https://zhuanlan.zhihu.com/p/28994731)

## 以太币供应

- [以太坊的发行模式](https://blog.ethereum.org/2014/04/10/the-issuance-model-in-ethereum)
- [澄清以太币供应和燃料成本](https://www.reddit.com/r/ethereum/comments/44zy88/clarification_on_ether_supply_and_cost_of_gas/)
- [关于以太坊稀缺的问题及其通货膨胀或通货紧缩的性质](https://www.reddit.com/r/ethereum/comments/45vj4g/question_about_scarcity_of_ethereum_and_its/)
- [有没有像btc一样的帽子，有多少以太币可以被开采？](https://www.reddit.com/r/ethtrader/comments/48yqg6/is_there_a_cap_like_with_btc_with_how_many_ether/)

## 获取以太币

请看到[这个页面](https://github.com/ethereum/wiki/wiki/Getting-Ether).

## 发送以太币

[以太坊钱包](https://github.com/ethereum/mist/releases)支持通过图形界面发送到以太网。

以太币也可以使用**geth控制台**进行交易.

    ::: console
    > var sender = eth.accounts[0];
    > var receiver = eth.accounts[1];
    > var amount = web3.toWei(0.01, "ether")
    > eth.sendTransaction({from:sender, to:receiver, value: amount})

有关以太网转账交易的更多信息，请参阅[帐户类型燃料交易](contracts-and-transactions/account-types-gas-and-transactions.md)。

以太坊在加密货币领域是独一无二的，因为以太币具有作为加密燃料的效用价值，通常被称为“燃料”。
除交易费外，燃料是每个网络请求的核心部分，并要求发件人支付所消耗的计算资源。
燃料成本是根据请求的数量和复杂程度并乘以当前的燃料价格来动态计算的。
其作为加密燃料的价值，增加了以太币和以太坊整体的稳定性和长期需求。
有关更多信息，请参阅[帐户类型燃料和交易](contracts-and-transactions/account-types-gas-and-transactions.md)。

## 燃料和以太币

- [有人能解释一下以太坊燃料的概念吗？](https://www.reddit.com/r/ethereum/comments/271qdz/can_someone_explain_the_concept_of_gas_in_ethereum/)
- [有人可以解释一下燃料价格的概念吗？](https://www.reddit.com/r/ethereum/comments/3fnpr1/can_someone_possibly_explain_the_concept_of/)
- [以太币可以用作货币吗？ELI5以太币，气体和硬币供应给我。](https://www.reddit.com/r/ethereum/comments/49gol3/can_ether_be_used_as_a_currency_eli5_ether_gas/)

燃料应该是网络资源/利用的不变成本。,您希望发送交易的实际成本总是相同的，所以您不能真正期望燃料发行，货币一般是不稳定的。

因此，我们发行价值应该有所不同的以太，而且要以以太计算燃料价格。 如果以太币价格上涨，以以太币计的燃料价格应该下调，以保持燃料的实际成本相同。

燃料有多个相关术语: 燃料价格，燃料成本，燃料价格和煤气费。 燃料背后的原理是对于以太坊网络的交易或计算成本有多少稳定的价值。

- 燃料成本是燃料计算成本的一个静态值, 其意图是燃料的真正价值从不改变, 所以这个成本应该始终保持稳定.
- 燃料价格是多少燃料成本在另一个货币或像以太币的象征。 为了稳定燃料的价值， 燃料价格是一个浮动价值，如果代币或货币的成本波动, 燃料价格变化保持相同的实际价值. 燃料价格是由用户愿意花费的均衡价格决定的, 以及多少处理节点愿意接受.
- 燃料限制是每块可以使用的最大燃料量, 它被认为是最大的计算量, 交易量, 或块的大小, 矿工可以随着时间的推移慢慢改变这个值.
- 燃料费实际上是运行特定交易或计划（称为合约）所需支付的燃料量. 块的燃料费用可以用来暗示块的计算负荷，交易量或大小。 燃料费用支付给矿工（或PoS保税承包商）。

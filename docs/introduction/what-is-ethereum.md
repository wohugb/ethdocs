# 以太坊

请注意，本网站上的一些信息可能不再相关或过时。
您也可以参考[以太坊wiki](https://github.com/ethereum/wiki)获取最新信息。

## 什么是以太坊

以太坊是一个开放的区块链平台，允许任何人建立和使用在区块链技术上运行的分散的应用程序。
和比特币一样，没有人控制或拥有以太坊 - 这是一个由世界各地许多人建立的开源项目。
但是与比特币协议不同的是，以太坊被设计成具有适应性和灵活性。
在以太坊平台上创建新的应用程序很容易， 使用[家园版](homestead-release), 任何人使用这些应用程序现在都是安全的.

## 下一代区块链

区块链技术是比特币的技术基础, 首先由其神秘作家中本聪在他的白皮书“比特币：对等电子现金系统”中描述, 2008年出版.
原始论文中已经讨论了区块链用于更广泛的用途, 直到几年后，区块链技术才成为一个通用术语.
区块链是一种分布式计算架构，每个网络节点都执行和记录相同的事务,它们被分组成块.
一次只能添加一个块, 每个块都包含一个数学证明，它从前一个块开始依次排列.
这样，区块链的“分布式数据库”在整个网络上保持一致。
个人用户与分类帐（交易）的交互通过强大的加密技术来保证。
维护和验证网络的节点通过编码到协议中的数学实施的经济激励来激励。

在比特币的情况下，分布式数据库被认为是账户余额表, 分类帐, 而交易是比特币代币的转移，以促进个人之间的可靠融资.
但是，比特币开始吸引更多的开发者和技术人员的关注, 新颖的项目开始使用比特币网络，而不是传递价值代币。
其中许多采取“alt硬币”的形式 - 单独的区块链与自己的加密货币，改进了原来的比特币协议，以增加新的特性或功能。

在2013年末，以太坊的发明家Vitalik Buterin提出，能够重新编程以执行任意复杂计算的单个区块链可能包含许多其他项目。

2014年， 以太坊创始人Vitalik Buterin，Gavin Wood和Jeffrey Wilcke开始了下一代区块链的工作，他们的目标是实现一个通用的，完全不受信任的智能合约平台。

## 以太坊虚拟机

以太坊是一个可编程的区块链。
而不是给用户一套预定义的操作（比如比特币交易）, 以太坊允许用户创建自己想要的复杂操作。
通过这种方式， 它作为许多不同类型的分散式区块链应用程序的平台, 包括但不限于加密货币。

以太坊在狭义上是指为分散式应用定义平台的一套协议。
它的核心是[以太坊虚拟机（“EVM”）<the-EVM>], 它可以执行任意算法复杂度的代码。
在计算机科学方面，以太坊是“图灵完整”的。
开发人员可以使用以JavaScript和Python等现有语言为模型的友好编程语言来创建在EVM上运行的应用程序。

像任何区块链一样，以太坊还包括一个点对点网络协议。
以太坊区块链数据库由连接到网络的许多节点维护和更新。
网络的每个节点都运行EVM并执行相同的指令。
出于这个原因，以太坊有时被形容为“世界电脑”。

整个以太坊网络的计算大规模并行化并没有使计算更有效率。
事实上，这个过程使以太坊的计算远比传统的“计算机”慢得多，也更昂贵。
相反，每个以太坊节点都运行EVM，以便在整个区块链中保持一致。
分散的共识使得以太坊的容错能力达到极致，保证了零停机时间，并使存储在区块链中的数据永远不变，并保持审查。

以太坊平台本身是没有特色的，或者是价值不可知的。
与编程语言类似，企业家和开发人员决定应该如何使用它。
但是，很显然某些应用程序类型比以太坊的功能更有益于其他应用程序。
具体而言，以太坊适用于自动化对等之间的直接交互或促进整个网络中协调的群组操作的应用。
例如，协调对等市场的应用程序或复杂金融合约的自动化。
比特币允许个人交换现金，而不涉及金融机构，银行或政府等中间商。
以太坊的影响可能更为深远。
理论上讲，使用以太坊上运行的代码可以自动，可靠地进行财务交互或任何复杂的交换。
除了财务应用之外，任何信任，安全和永久性都很重要的环境，例如资产登记，投票，治理和物联网等，都可能受到以太坊平台的巨大影响。

## 以太坊如何工作？

以太坊结合了比特币用户所熟悉的许多特性和技术，同时也引入了许多自己的修改和创新。

而比特币区块链纯粹是一个交易清单，[以太坊的基本单位是账户<Accounts>].
以太坊区块链跟踪每个账户的状态，以太坊区块链上的所有状态转换都是账户之间的价值和信息转移。
有两种类型的帐户：

- 外部拥有的帐户（EOAs），由私钥控制
- 合约账户由合约代码控制，只能由EOa“激活”。对于大多数用户来说，这两者之间的基本区别在于，人类用户控制EOAs，因为他们可以控制对EOA进行控制的私钥。

合约账户则由其内部代码进行管理。
如果它们是由用户“控制”的，那是因为它们被编程为由具有特定地址的EOA来控制，而EOA又由持有控制该EOA的私钥的人来控制。

流行术语“智能合约”是指合约账户中的代码 - 当交易被发送到该账户时执行的程序。
用户可以通过将代码部署到区块链来创建新的合约。

合约账户只能在EOA指示的情况下执行操作。
所以合约账户不可能执行像随机数字生成或API调用这样的本地操作 - 只有在EOA提示的情况下，才能执行这些操作。
这是因为以太坊要求节点能够就计算结果达成一致，这就要求严格确定执行的保证。

像比特币一样，用户必须向网络支付小额交易费用。
这可以保护以太坊区块链免受轻微或恶意的计算任务，如DDoS攻击或无限循环。
交易的发送者必须支付他们激活的“程序”的每一步，包括计算和内存存储。
这些费用是以以太坊的本地价值，以太币来支付的。

这些交易费用由验证网络的节点收集。
这些“矿工”是以太坊网络中接收，传播，验证和执行交易的节点。
然后，矿工将这些交易（包括以太坊区块链中账户“状态”的许多更新）分组到所谓的“块”中，
矿工每获得一个成功的矿块都会得到乙醚奖励。
这为人们将硬件和电力奉献给以太坊网络提供了经济激励。

就像比特币网络一样，矿工的任务是解决一个复杂的数学问题，以便成功地“挖掘”一个块。
这被称为“工作证明”。
任何计算问题需要数量级的更多的资源来解决算法，比验证解决方案是一个很好的候选人的工作证明。
为了阻止由于使用专用硬件（例如[ASIC]（<https://en.bitcoin.it/wiki/ASIC>））而导致的集中化，就像在比特币网络中发生的那样，以太坊选择了一种基于内存的，,难以计算的问题。
如果问题需要内存以及CPU，那么理想的硬件实际上就是通用计算机。
这使得以太坊的工作证明ASIC具有抵抗性，从而使分布式安全性比区块链更为分散，而区块链的挖掘由像比特币这样的专业硬件来控制。

### 了解以太坊

[待扩展]

#### 有一些悲伤的公关视频：

- [以太坊：世界电脑](https://www.youtube.com/watch?v=j23HnORQXvs)
- [以太坊 - 轮到你了](https://vimeo.com/88959651)

#### 区块链和以太坊101

- [解释像我这样的比特币](https://medium.com/@nik5ter/explain-bitcoin-like-im-five-73b4257ac833) - 一个很好的介绍区块链技术和比特币的轻度tech savvy非专业人员。
- [一个简单的以太坊视图](https://medium.com/@creole/7-a-simple-view-of-ethereum-e276f76c980b)
- [解释ethereum](https://blog.chain.com/explaining-ethereum-fd043c7d602e)
- [stackexchange上向非技术人员解释以太坊问题](http://ethereum.stackexchange.com/questions/45/how-would-i-explain-ethereum-to-a-non-technical-friend)
- ELI5以太坊的Reddit线程:

[1](https://www.reddit.com/r/ethereum/comments/43brik/explaining_ethereum_to_friends/)
[2](https://www.reddit.com/r/ethereum/comments/3c132d/eli5_what_you_guys_do_here/)
[3](https://www.reddit.com/r/ethereum/comments/1vvz13/eli5_ethereum/)
[4](https://www.reddit.com/r/ethereum/comments/1vb1gc/is_ethereum_an_alt_coin_can_anyone_eli5/)
[5](https://www.reddit.com/r/ethereum/comments/4279dh/eli5_what_exactly_is_ethereum/)
[6](https://www.reddit.com/r/ethereum/comments/2hl10p/eli5_ethereum/)
[7](https://www.reddit.com/r/ethereum/comments/41y8by/the_best_way_i_can_eli5_ethereum_to_someone/)
[8](https://www.reddit.com/r/ethereum/comments/44b69e/i_dont_understand_the_technology/)
[9](https://medium.com/@nik5ter/explain-bitcoin-like-im-five-73b4257ac833)
[10](https://www.reddit.com/r/ethereum/comments/1vb1gc/is_ethereum_an_alt_coin_can_anyone_eli5/)
[11](https://www.reddit.com/r/ethereum/comments/2dpgwy/eli5_ethereum/)
[12](https://www.reddit.com/r/ethereum/comments/47u5y9/explain_what_ethereum_is_to_a_bitcoin_trader/)
[13](https://www.reddit.com/r/ethereum/comments/27wsgq/eli5_ethereum_its_uses_its_features_its_future/)
[14](https://www.reddit.com/r/ethereum/comments/4936d3/are_you_new_to_ethereum_here_are_many/)
[15](https://www.reddit.com/r/ethereum/comments/4279dh/eli5_what_exactly_is_ethereum/)
[16](https://www.reddit.com/r/ethereum/comments/3n37dp/explaining_ethereum_ecosystem_for_normal/)
[17](https://www.reddit.com/r/ethereum/comments/271qdz/can_someone_explain_the_concept_of_gas_in_ethereum/)
[18](https://www.reddit.com/r/ethereum/comments/3hg7id/why_should_the_average_person_care_about_ethereum/)
[19](https://www.reddit.com/r/ethereum/comments/43exre/what_are_the_advantages_of_ethereum_over_other/)

#### 影片

- [以博士木材为特色的世界计算机以太坊](http://change.is/video/ethereum-the-world-computer-featuring-dr-gavin-wood)

#### 信息图表

![以太坊解释...[给你妈妈]](https://blog.ethereum.org/wp-content/uploads/2015/06/Ethereum-image-infographic-beginners-guide.png)
![](http://decentral.ca/wp-content/uploads/2016/03/infographic.jpg)
![](https://medium.com/@angelomilan/ethereum-explained-to-my-mom-infographic-673e32054c1c#.n9kzhme6v)

#### 比较交替

- [NXT](https://www.reddit.com/r/ethereum/comments/23aejv/eli5_what_is_the_qnce_between_ethereum_and/)
- [女仆安全](https://www.reddit.com/r/ethereum/comments/22r49u/how_is_maidsafe_different_then_etherium/)

# 常见问题

??? faq "什么是以太坊？"

    以太坊是一个分散的智能合约平台，由一个名为Ether的加密货币提供支持。 了解更多可以阅读"[什么是以太坊](introduction/what-is-ethereum.md)"页面。

??? faq "我听说过以太坊， 但是Geth，Mist，Ethminer，Mix是什么？"

    - **Geth**: 这是一个以太坊节点的实现，并且是与以太坊区块链进行互动的基础。
        通过本地运行，您可以轻松地与以太坊区块链进行交互。
        阅读 [go-ethereum安装说明](https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum).
    - **Mist**: 这相当于一个网页浏览器， 但是对于以太坊平台。
        它充当一个GUI来显示您与之交互的账户和合约。
        它还允许您在图形用户界面中创建合约并与其进行交互，而无需触摸命令行。
        如果您不是开发人员，只想存储以太和与以太坊合约进行交互，那么Mist就是要使用的程序。
        下载可以在[Mist发布页面](https://github.com/ethereum/mist/releases)上找到.
    - **Ethminer**: 一个独立的挖矿机。 这可以用来挖掘或基准采矿设备。 它与eth，geth和pyethereum兼容。 查看[采矿]页面了解更多信息。
    - **Mix**: DApp创作的集成开发环境。在Ethereum平台上快速构建和调试分散式应用程序。更多的信息可以在[混合GitHub页面](https://github.com/ethereum/mix).

??? faq "如何将大文件存储在区块链中？"

    一般来说，由于存储成本高昂，您不希望在以太坊区块链中存储大型文件或数据片段。 你会需要使用第三方存储解决方案，如Swarm或IPFS。 Swarm是用于分布式文件存储的以太坊特定项目。 IPFS是一个与以太坊关系密切的非以太坊项目; 未来它会被使用独立并可能被用作在Swarm中的一个附加层。 有关更多信息，请参见[以太坊StackExchange主题]   (http://ethereum.stackexchange.com/questions/1000/what-are-some-proposed-ways-of-storing-data-in-ethereum/1001#1001)。

??? faq "以太坊是以比特币为基础的吗？"

    只是在它使用区块链的意义上说, 比特币是开创性的.以太坊有一个独立的区块链，与比特币区块链有几个重大的技术差异.有关详细说明，请参阅[以太坊StackExchange答案](http://ethereum.stackexchange.com/questions/700/what-are-the-differences-between-bitcoin-blockchain-and-ethereum-blockchain).

??? faq "以太坊的未来是什么？"

    以太坊开发商计划在未来从工作证明共识模型转换为证明共识模型。
    他们还在研究可伸缩性解决方案以及如何在区块链上存储秘密。

??? faq "账户和“钱包合约”有什么区别?"

    一个帐户是您的公钥/私钥对文件，作为您在区块链上的身份。请参阅术语表中的“帐户”。
    “钱包合约”是一个以太坊合约，通过多重签名和程序化的存取款限制等功能来保护您的以太和身份。
    在Mist Ethereum 钱包 GUI 客户端中可以轻松创建钱包合约。

??? faq "密钥文件是否只能从您下载客户端的计算机上访问？"

    不，您可以导出或移动密钥文件，但请始终记住备份您的密钥文件，并注意您将密钥文件存储在哪台计算机上。

??? faq "下载区块链需要多长时间？"

    以太坊区块链持续增长，截至2016年3月，接近10GB。
    下载所花费的时间取决于您可以连接到的对等的数量，您的Internet连接速度以及其他因素。
    查看[download-the-blockchain-faster]部分，了解有关快速同步区块链的提示。

??? faq "如何获取进出地址的交易清单？"

    您必须手动从区块链中取出交易才能实现此目的。
    或者，你可以依赖第三方的探索者的API，如[Etherchain](https://etherchain.org/apidoc).
    但是，对于合约执行交易，您可以过滤合约日志以实现此目的。

??? faq "合约可以支付执行的费用吗?？"

    不，这是不可能的。 用于执行的燃料必须由提交执行请求的地址提供。

??? faq "合约可以调用另一份合约吗？"

    是的，这是可能的，阅读[关于合约之间的交互](https://dappsforbeginners.wordpress.com/tutorials/interactions-between-contracts/).

??? faq "交易可以离线签署，然后在另一台在线设备上提交吗？"

    是的，你可以参考从[冰箱](https://github.com/ConsenSys/icebox)的解决方案.

??? faq "如何获得测试网络以太网？"

    见[测试网络]。

??? faq "交易是否可以由第三方发送？ 即交易广播可以外包"

    技术上是的，但有一个重要的限制，而不是比特币签署的交易: 在ethereum交易有nonce
    (更确切地说，每个账户在发送交易时根据总共发送了多少交易而增加计数器。如果有3笔交易已经从账户发送，那么账户现时值为3).

??? faq "以太坊合约是否可以使用第三方API来提取数据？"

    不，以太坊合约不能以这种方式从外部信息源获取数据。
    然而，有可能通过交易将来自外部站点（例如天气站点，股票价格）的数据推送到以太坊合约。
    有一些“以太网”服务与以太网网络兼容，可以将数据推送/推送到以太坊网络收费。

??? faq "通过以太坊网络发送的数据和合约的内容是否加密？"

    以太坊网络上的数据和合约都是编码的，但没有加密。
    每个人都可以审计合约的行为和发送给他们的数据。
    但是，在将数据广播到网络之前，您始终可以自由地对数据进行加密。

??? faq "我能在以太网络上储存秘密或密码吗?？"

    以太坊的所有数据都是公开的。
    以太坊合约中不可能存储秘密或密码而不被所有人看到。
    有一些工作正在通过代码混淆和其他技术来实现。
    可以阅读Vitalik Buterin写的一篇好文“[区块链上的隐私权](https://blog.ethereum.org/2016/01/15/privacy-on-the-blockchain/)”。

??? faq "以太坊如何打击采矿池集中？"

    基于以太坊PoW的共识算法有两个主要的方法来对抗集中挖掘 ([源](http://ethereum.stackexchange.com/questions/549/how-does-ethereum-avoid-mining-pool-centralization)).

    -   首先是通过减少由于孤立矿井造成的损失，这是独立矿工更可能经历的。
        -   以太坊采矿算法的这一部分, 一种被称为GHOST的技术,
            只包括最近的孤立块的标题，作为对块生产者和（孤立的）块的包括者的减少的回报的回报。
            这些包括来自“祖父母”或更早的块的孤儿经常被称为“叔叔”块，因为性别中性术语“ommer”没有被广泛知道或理解。
    -   以太坊PoW共识算法与采矿中心化的对抗的第二种方式是使用抗ASIC功能的功劳证明（Proof of Work）功能。
        -   通过防止采矿被专门设计和生产的硬件所支配，独立的矿工们保持竞争力，
            甚至在利润和/或硬件投资水平上占有优势, 因为他们可以利用现成的商品硬件 (即消费者图形卡).

??? faq "以太坊将如何处理不断增长的区块链大小？"

    围绕区块链可扩展性进行了许多讨论。 这个问题的部分地回答在[这个以太坊StackExchange](http://ethereum.stackexchange.com/questions/521/what-does-it-mean-to-run-code-on-the-blockchain-wouldnt-blockchain-become-hu)和[这个来自Vitalik Buterin的博客文章](https://blog.ethereum.org/2014/02/18/ethereum-scalability-and-decentralization-updates/).

??? faq "以太坊将如何确保网络每秒能够进行10,000次以上的交易？"

    以太坊正在计划在其发展路线图的宁静阶段实施证据共识协议变更。 有关可能的以太坊PoS候选人的更多信息以及如何增加每秒交易次数可以[在这里找到](https://blog.ethereum.org/2015/08/01/introducing-casper-friendly-ghost/).

??? faq "合约在哪里"

    TODO

??? faq "你的问题还没有回答？"

    请问社区[以太坊StackExchange](http://ethereum.stackexchange.com/).

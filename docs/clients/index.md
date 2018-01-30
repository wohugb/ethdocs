# 选择客户端

## 为什么有多个以太坊客户？

从项目早期开始，就有多种不同操作系统的客户端实现。
客户的多样性是整个生态系统的巨大胜利。
它让我们验证协议(在[黄皮书](https://github.com/ethereum/yellowpaper)中指定)是明确的。
它为新的创新敞开了大门。
这使我们都诚实。
然而，最终用户可能会感到困惑，因为没有通用的“以太坊安装者”供他们使用。

截至2016年9月，领先的实施是[go-ethereum]和[Parity]。

|客户端             |语言      |开发商                                  |最新版本|
|-|-|-|-|
|[go-ethereum]     |Go       |[Ethereum Foundation][foundation]      |[go-ethereum-v1.4.18][go-ethereum-v1.4.18]
|[Parity]          |Rust     |[Ethcore](https://ethcore.io/)         |[Parity-v1.4.0][parity-v1.4.18]
|[cpp-ethereum]    |C++      |[Ethereum Foundation][foundation]      |[cpp-ethereum-v1.3.0][cpp-ethereum-v1.4.18]
|[pyethapp]        |Python   |[Ethereum Foundation][foundation]      |[pyethapp-v1.5.0][pyethapp-v1.5.0]
|[ethereumjs-lib]  |js       |[Ethereum Foundation][foundation]      |[ethereumjs-lib-v3.0.0][ethereumjs-lib-v3.0.0]
|[Ethereum(J)]     |Java     |[<ether.camp>](http://www.ether.camp)  |[ethereumJ-v1.3.1][ethereumJ-v1.3.1]
|[ruby-ethereum]   |Ruby     |[Jan Xie](https://github.com/janx/)    |[ruby-ethereum-v0.9.6][ruby-ethereum-v0.9.6]
|[ethereumH]       |Haskell  |[BlockApps](http://www.blockapps.net/) |no Homestead release yet

[foundation]: https://ethereum.org/foundation
[go-ethereum-v1.4.18]:
[parity-v1.4.18]: https://github.com/ethereum-thereum/releases/tag/v1.4.18
[cpp-ethereum-v1.4.18]: https://github.com/ethcore/parity/releases/tag/v1.4.0
[pyethapp-v1.5.0]: https://github.com/ethereum/pyethapp/release/v1.5.0
[ethereumjs-lib-v3.0.0]: https://github.com/ethereumhereumjs-lib/releases/tag/v3.0.0
[ethereumJ-v1.3.1]: https://github.com/ethereum/ethereumj/releases/tag/1.3.1
[ruby-ethereum-v0.9.6]: https://rubygemrg/gems/ruby-ethereum/versions/0.9.6

## 我应该在桌面/笔记本电脑上安装什么？

大多数用户可能会安装[Mist / Ethereum钱包](https://github.com/ethereum/mist)，这将足够满足他们的需求。

以太坊钱包是** Mist浏览器**的“单一的dapp”部署，这将是大都会发展阶段的核心，

Mist带有捆绑的[go-ethereum]和[cpp-ethereum]二进制文件，如果你在Mist启动时没有运行命令行以太坊客户端，
如果你想使用喷Mist奇偶，或者在专用网络上运行喷Mist，只需在喷Mist之前启动节点，而喷Mist将连接到你的节点

**Work is underway to add Parity and other clients as "first-class entities" to Mist too.**

如果你想在命令行中与Ethereum交互，并利用Javascript控制台，那么你将需要安装一个客户端
按照上表中的链接进一步说明。

如果你想开采，那么Mist将是不够的。
查看[采矿]部分。

## 我应该在手机/平板电脑上安装什么？

我们刚刚开始支持移动设备。
Go团队正在发布实验性的iOS和Android库，一些开发人员正在使用这些库开始引导移动应用程序，但还没有任何可用的移动Ethereum客户端。

在移动设备上使用以太坊的主要障碍是Light Client支持仍然不完整。
已经完成的工作是在私人分支，只有Go客户端可用。
doublethinkco将在接下来的几个月内开始为C ++客户开发Light Client。

查看[Status.im](http://status.im)，最初使用[ethereumj-personal](https://github.com/status-im/ethereumj-personal)基于[Ethereum(J) ,]，但最近翻转到与Light Client交叉构建。

## 我应该在我的SBC上安装什么？

你有一些选择，这取决于你的技能水平，以及你正在做什么。

- 下载完整准备的图像(链接到页面，提供详细的下载和安装说明)
  - 如果你是新来的以太坊和SBC董事会，如树莓派，那么这是给你的！,只需下载特定于您正在使用的开发板的图像，将其刻录到SD卡，引导设备并运行以太坊！
- 下载预编译的应用程序(链接到页面，提供详细的下载和安装说明)
  - 如果你已经有一个SBC运行，并有一个特定的，首选的操作系统或设置，你想保持，那么这是你最好的选择！,根据平台的不同，您可以简单地下载相应的可执行文件，并且只需将库和PATH设置的链接最小化，就可以在现有环境中运行以太坊。
- 从源代码使用可定制的脚本(链接到更多的细节和单个SBC链接到[链接](https://github.com/ethembedded))
  - 希望执行自定义安装？,我们有脚本可以从“在设备上”进行编译。我们的脚本包含自动安装的依赖关系以及客户端本身。
    这将允许您安装以太坊客户端的特定版本(i.e.-"develop", "master", etc.), 编译你自己的分支版本的客户端, 而且一般都是在构建过程中错综复杂的。

## 与客户互动

为了以编程方式与以太坊客户端进行交互，请参阅[正在连接客户端]部分。

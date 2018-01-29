# CPU挖矿

您可以使用您的计算机的中央处理单元（CPU）来挖掘以太。
T他不再有利可图，因为GPU矿工的效率大约高出两个数量级。
然而，您可以使用CPU在莫登测试网或私有链上挖掘，以创建您需要测试合约和交易的以太币，而无需在实时网络上花费您的实际的时间。

!!! note "Note"

    除了用于测试目的之外，测试网络没有任何价值（参见[测试网络]）。

## 使用geth

当你用`geth`启动你的ethereum节点时，默认情况下不挖矿。
以CPU采矿模式启动, 你需要使用`--mine` [命令行选项](https://github.com/ethereum/go-ethereum/wiki/Command-Line-Options).
`-minerthreads`参数可用于设置并行挖掘线程数（默认为处理器内核总数）。

`geth --mine --minerthreads=4`

您也可以在运行时使用[console](https://github.com/ethereum/go-ethereum/wiki/JavaScript-Console#adminminerstart)启动和停止CPU挖掘，.
`miner.start`为矿工线程的数量提供了一个可选的参数。

```js
> miner.start(8)
true
> miner.stop()
true
```

请注意，只有在与网络同步的情况下（因为您是在一致性块之上进行挖掘），真正的以太网挖掘才有意义。
因此，eth blockchain下载器/同步器将延迟挖掘，直到同步完成, 之后，挖掘自动开始，除非你用`miner.stop()`取消你的意图。

为了赚取乙醚，你必须有你的** etherbase **（或** coinbase **）地址集。
这个etherbase默认为您的主帐户。
如果你没有etherbase地址，那么`geth -mine`将不会启动。

你可以在命令行上设置你的etherbase：

```bash
geth --etherbase 1 --mine  2>> geth.log // 1 is index: second account by creation order OR
geth --etherbase '0xa4d8e9cae4d04b093aac82e6cd355b6b963fb7ff' --mine 2>> geth.log
```

你也可以在控制台上重置你的etherbase：

```js
miner.setEtherbase(eth.accounts[2])
```

请注意，您的etherbase不需要是本地帐户的地址，只是现有帐户的地址。

有一个选项[可以添加额外的数据](https://github.com/ethereum/go-ethereum/wiki/JavaScript-Console#minersetextra)（只有32个字节）到您的开采块。
按照惯例，这被解释为unicode字符串，所以你可以设置你的短虚拟标签。

```js
miner.setExtra("ΞTHΞЯSPHΞЯΞ")
...
debug.printBlock(131805)
BLOCK(be465b020fdbedc4063756f0912b5a89bbb4735bd1d1df84363e05ade0195cb1): Size: 531.00 B TD: 643485290485 {
NoNonce: ee48752c3a0bfe3d85339451a5f3f411c21c8170353e450985e1faab0a9ac4cc
Header:
[
...
        Coinbase:           a4d8e9cae4d04b093aac82e6cd355b6b963fb7ff
        Number:             131805
        Extra:              ΞTHΞЯSPHΞЯΞ
...
}
```

你可以用[miner.hashrate](https://github.com/ethereum/go-ethereum/wiki/JavaScript-Console#adminminerhashrate)来检查你的哈希率, 结果是H/s（每秒哈希操作）.

```js
> miner.hashrate
712000
```

在你成功地开采了一些块之后，你可以检查你的etherbase帐户的ether平衡。
现在假设你的etherbase是一个本地帐户：

```js
> eth.getBalance(eth.coinbase).toNumber();
'34698870000000'
```

为了把你的收入花在煤气上进行交易, 您将需要解锁此帐户。

```js
> personal.unlockAccount(eth.coinbase)
Password
true
```

您可以使用控制台上的以下代码片段来检查特定矿工（地址）挖掘哪些块：

```js
function minedBlocks(lastn, addr) {
  addrs = [];
  if (!addr) {
    addr = eth.coinbase
  }
  limit = eth.blockNumber - lastn
  for (i = eth.blockNumber; i >= limit; i--) {
    if (eth.getBlock(i).miner == addr) {
      addrs.push(i)
    }
  }
  return addrs
}
// 扫描最后的1000个块，并返回由您的coinbase开采的块的块编号
// (更精确地阻止发送给你的coinbase的挖矿奖励).
minedBlocks(1000, eth.coinbase);
//[352708, 352655, 352559]
```

请注意，它会经常发生，你找到一个块，但它永远不会对规范链。
这意味着当你在当地包括你的雷区, 当前状态将显示挖掘奖励记入您的帐户, 然而，过了一段时间， 发现更好的链条，我们切换到不包含您的区块的链条，因此不记录挖掘奖励。
因此，监测矿工平衡的矿工很可能会发现它可能会波动很多。
# 帐户管理

## 帐号

帐户在以太坊中扮演着重要角色。
有两种类型的账户：*外部拥有账户*(EOAs)和*合约账户*。
这里我们将重点放在外部拥有的账户上，简称为*账户*。
合约账户将被称为*合约*，并[在合约<合约>中详细讨论]。
这种通用的账户概念包含了外部拥有的账户和合约，这是合理的，因为这些实体被称为*状态对象*。
这些实体有一个状态：账户有余额，合约有余额和合约存储。
所有帐户的状态都是以太坊网络的状态，每个区块都会更新，网络真正需要哪个网络
账户对于用户通过交易与以太坊区块链进行交互至关重要。

如果我们将以太坊仅限于外部拥有的账户，并且只允许它们之间的交易，我们就会到达一个阿尔特币系统

帐户表示外部代理的身份(例如，人类角色，挖掘节点或自动代理)。
账户使用公钥加密来签署交易，以便EVM可以安全地验证交易发件人的身份。

## 密钥文件

每个账户都由一对密钥，一个私钥和一个公钥来定义。
帐户通过其*地址*进行索引，该地址由公钥通过取最后的20个字节而得出。
每个私钥/地址对都以* keyfile *编码。
密钥文件是可以在任何文本编辑器中打开和查看的JSON文本文件。
密钥文件的关键组成部分(您的帐户的私钥)始终是加密的，并使用您的密码进行加密
密钥文件位于您以太坊节点数据目录的`keystore`子目录中。
确保定期备份你的密钥文件！,有关更多信息，请参见[备份和还原帐户]部分。

创建一个密钥等于创建一个帐户:

- 你不需要告诉其他人你正在做这件事
- 您不需要与区块链同步
- 你不需要运行一个客户端
- 你甚至不需要连接到互联网

当然你的新账户不会包含任何以太网。
当然你的新账户不会包含任何以太网。

在以太坊节点之间传输整个目录或任何单独的密钥文件是安全的。

!!! Warning

    请注意，如果您将密钥文件从不同节点添加到节点，帐户顺序可能会更改。
    因此，请确保您不依赖或更改脚本或代码片段中的索引。

## 创建帐户

!!! Warning

    为了从一个账户发送交易，包括发送以太，你必须同时拥有密钥文件和密码。
    请务必保留密钥文件的副本并记住该密钥文件的密码，并尽可能安全地存储它们。
    这里没有逃生路线;,丢失密钥文件或忘记密码，并且所有以太网都消失了。
    没有密码就无法访问您的帐户，并且这里没有*忘记我的密码*选项。
    别忘记了。

### 运行命令

一旦你安装了geth客户端，创建一个帐户只是在终端中执行`geth account new`命令的一个例子。

请注意，您不必运行geth客户端或与区块链同步以使用`geth account`命令。

```bash
$ geth account new

  Your new account is locked with a password.Please give a password.Do not forget this password.
  Passphrase:
  Repeat Passphrase:
  Address: {168bc315a2ee09042d83d7c5811b533620531f67}
```

对于非交互式使用，您需要提供明文密码文件作为`--password`标志的参数。
该文件中的数据由密码的原始字节组成，后面紧跟一个换行符。

```bash
$ geth --password /path/to/password account new
```

!!! Warning

    使用`--password`标志仅用于受信任环境中的测试或自动化。
    将密码保存到文件或以任何其他方式公开它是个不错的主意。
    如果确实在密码文件中使用了“--password”标志，请确保该文件对于除您以外的任何人都不可读或甚至不可列出。
    您可以在Mac / Linux系统中通过以下方式实现此目的：

```bash
touch /path/to/password
chmod 600 /path/to/password
cat > /path/to/password
>I type my pass
```

要使用`geth account`命令的`list`子命令列出当前位于`keystore`文件夹中的所有密钥文件帐户：

```bash
$ geth account list

account #0: {a94f5374fce5edbc8e2a8697c15331677e6ebf0b}
account #1: {c385233b188811c9f355d4caec14df86d6248235}
account #2: {7f444580bfef4b9bc7e14eb7fb2a029336b07c9d}
```

密钥文件的文件名格式为`UTC  -  <created_at UTC ISO8601>  -  <address hex>`。 上市时的账户顺序是字典式的，但作为时间戳格式的结果，它实际上是创建的顺序。

### 使用控制台

为了使用geth创建一个新的帐户，我们必须首先在控制台模式下启动geth(或者你可以用`geth attach`把一个控制台附加到一个已经运行的实例上)：

```bash
> geth console 2>> file_to_log_output
instance: Geth/v1.4.0-unstable/linux/go1.5.1
coinbase: coinbase: [object Object]
at block: 865174 (Mon, 18 Jan 2016 02:58:53 GMT)
datadir: /home/USERNAME/.ethereum
```

控制台允许您通过发出命令与本地节点进行交互。,例如，尝试命令列出您的帐户：

```js
> eth.accounts

{
    code: -32000,
    message: "no keys in store"
}
```

这表明你没有帐户。您也可以从控制台创建一个帐户：

```js
> personal.newAccount()
Passphrase:
Repeat passphrase:
"0xb2f69ddf70297958e582a0cc98bce43294f1007d"
```

!!! Note

    请记住使用强大且随机生成的密码。

我们刚刚创建了第一个帐户。如果我们试图再次列出我们的帐户，我们可以看到我们的新帐户：

```js
> eth.accounts
["0xb2f69ddf70297958e582a0cc98bce43294f1007d"]
```

### 使用Mist

对于厌恶命令行，现在有一个基于GUI的创建账户选项：“官方”Mist以太坊钱包。
在以太坊基金会的赞助下，Mist以太坊钱包和它的母亲Mist项目正在开发，因此是“官方”的地位。
钱包应用程序的版本适用于Linux，Mac OS X和Windows。

!!! Warning

    Mist钱包是beta软件。请小心使用，风险自负。

使用GUI Mist Ethereum钱包创建一个账户不是一件容易的事情。实际上，您的第一个帐户是在安装应用程序期间创建的。

1. [为应用程序下载最新版本的钱包应用程序](https://github.com/ethereum/mist/releases)。打开电子钱包应用程序将开始在计算机上同步以太坊区块链的完整副本，因为您实际上将运行完整的geth节点。
2. 解压下载的文件夹并运行Ethereum-Wallet可执行文件。

![downloading-mist](img/51Downloading.png){.align-center width="436px" height="352px"}

3. 打开电子钱包应用程序将开始在计算机上同步以太坊区块链的完整副本，因为您实际上将运行完整的geth节点。
4. 当您第一次启动Mist Ethereum钱包时，您会看到您在安装过程中创建的帐户。默认情况下，它将被命名为MAIN ACCOUNT(ETHERBASE)。

![opening-screen](img/51OpeningScreen.png){.align-center width="512px" height="469px"}

5. 创建额外的帐户很容易;,只需点击应用程序主屏幕上的添加帐户，然后输入所需的密码即可。

!!! Note

    Mist钱包仍在积极开发中，因此上述步骤的细节可能随升级而改变。

### 多重签名钱包

Mist以太坊钱包有一个选项，以确保您的钱包平衡与multisig钱包。
使用multisig钱包的好处是，它需要从多个帐户授权才能从余额中提取更多金额。
在创建多重钱包之前，您需要创建多个帐户。

在Mist中创建账户文件非常简单。
在“帐户”部分，点击“添加帐户”。
选择一个强大且易于记忆的密码(记住没有密码恢复选项)，确认它，然后创建您的帐户。
创建至少2个帐户。
如果您愿意，可以在运行Mist的单独计算机上创建辅助帐户(理论上，通过这种方式使您的多重身份更安全)。
创建多重钱包时，您只需要辅助帐户的公钥(您的存款地址)(复制/粘贴它们，千万不要手动输入)。
您的主帐户将需要创建multisig钱包合约，因此它必须位于您创建multisig钱包的计算机上。

现在您已经设置了帐户，请保持安全并备份(如果您的计算机崩溃，如果您没有备份，则会失去平衡)。
点击顶部菜单中的“备份”。
选择'keystore'文件夹，反面点击它/选择'copy'(不要选择'cut'，这将是非常糟糕的)。
导航至您的桌面，在空白区域中单击鼠标右键并选择“粘贴”。
您可能希望将此'keystore'文件夹的新副本重命名为'Ethereum -keystore-backup-year-month-day'等，以便您稍后快速识别它。
此时，您可以将文件夹内容添加到zip/rar文件中(如果在线备份，还可以使用另一个强大但易于记忆的密码对密码进行密码保护)，将其复制到USB驱动器，将其刻录到,CD/DVD，或将其上传到在线存储(Dropbox/Google Drive/等)。

您现在应该向您的主账户添加大约不低于0.02 ETH(您将开始创建账户的账户)
创建多重钱包合约时，这是交易费用所必需的。
另外还需要1个ETH(或更多)，因为Mist目前要求这样做才能保证钱包合约交易有足够的'燃料'来正确执行...所以对于初学者来说，总计不低于1.02 ETH。

在创建时，您将输入您附加到此multisig钱包的所有帐户的完整地址。
在进入Mist中的每个帐户的详细信息页面，并从右侧按钮列中选择“复制地址”后，我建议将每个地址复制/粘贴到纯文本编辑器(记事本/kedit/等)。
千万不要手动输入地址，否则冒着拼写错误的风险，并且可能会失去将余额发送到错误地址的交易。

我们现在准备创建multisig钱包。
在“电子钱包合约”下，选择“添加钱包合约”。
给它一个名字，选择主帐户所有者，然后选择'多重签名钱包合约'。
您会看到类似这样的内容：

这是由X个所有者控制的联合账户。
您每天最多可以发送X以太。
任何超过该限额的交易都需要X业主的确认。

无论您希望每日提款限额(只需要一个账户提取该金额)，以及需要多少所有者(账户)来核准任何提款金额，请设置您附加到此multisig钱包的任何数量的所有者(账户),超过每日限额。

现在添加您之前复制/粘贴到您的文本编辑器中的帐户的地址，确认您的所有设置都是正确的，然后点击底部的“创建”。
然后您需要输入密码才能发送交易。
在“电子钱包合约”部分，它应该显示您的新钱包，并说'创建'。

当钱包创建完成后，您应该在屏幕上看到您的合约地址。
选择整个地址，将其复制/粘贴到文本编辑器中的新文本文件中，然后将文本文件保存到桌面

现在，您只需备份“Ethereum-Wallet-Address.txt”文件，就像备份您的帐户文件一样，然后您

如果您要从备份中恢复，只需将'Ethereum -keystore-backup'文件夹中的文件复制到本演练的第一部分中提到的'keystore'文件夹中即可。
仅供参考，您可能需要创建'keystore'文件夹(如果它是以前从未安装过的机器上的全新安装的Mist)(第一次创建帐户时是创建此文件夹时)。
至于恢复多重钱包，而不是像我们之前在创建时那样选择“多签名钱包合约”，我们只需选择“导入钱包”。

故障排除：

- Mist不会同步。有效的解决方案之一就是将PC硬件时钟与NTP服务器同步，因此时间完全正确，然后重新启动。
- Mist同步后开始，但是是一个空白的白色屏幕。你有可能在基于Linux的操作系统(Ubuntu，Linux Mint等)上运行xorg视频驱动程序。尝试安装制造商的视频驱动程序。
- 错误的密码通知。这在目前的Mist版本上似乎是错误的通知。重新启动Mist，问题应该消失(如果你确实输入了正确的密码)。

### 使用Eth

与使用geth可用的密钥管理相关的每个选项都可以在eth中以相同的方式使用。

以下是与帐户相关的选项：

```js
> eth account list  // 列出钱包中的所有可用密钥。
> eth account new   // 列出钱包中的所有可用密钥。
> eth account update [<uuid>|<address> , ...]  // 对给定的密钥进行解密和重新加密。
> eth account import [<uuid>|<file>|<secret-hex>] // 从给定来源导入密钥并将其放置在钱包中。
```

以下是钱包相关选项：

```js
> eth wallet import <file> //Import a presale wallet.
```

!!! Note

    '账户导入'选项只能用于导入通用密钥文件。“钱包导入”选项只能用于导入预售钱包。

“钱包导入”选项只能用于导入预售钱包。

```js
> web3.personal
{
  listAccounts: [],
  getListAccounts: function(callback),
  lockAccount: function(),
  newAccount: function(),
  unlockAccount: function()
}
```

### 使用EthKey

*不建议使用!*

Ethkey是C ++实现的CLI工具，允许您与Ethereum钱包进行交互。
有了它，您可以列出，检查，创建，删除和修改密钥并检查，创建和签署交易。

我们假设您还没有在Aleth系列客户端运行诸如eth或其他任何客户端。
如果你有，你可以跳过这一节。
要创建钱包，请使用`createwallet`命令运行`ethkey`：

```bash
> ethkey createwallet
```

请输入MASTER密码以保护您的密码存储区(使其强大！)：系统会要求您提供主密码。
这可以保护您的隐私，并作为任何密钥的默认密码。
您需要再次输入相同的文字来确认。

!!! Note

    使用强大的随机生成的密码。

只需使用list命令即可列出钱包中的密钥：

```bash
> ethkey list

No keys found.
```

我们还没有创建任何密钥，它告诉我们！,我们来创建一个。

要创建密钥，我们使用`new`命令。
要使用它，我们必须传递一个名字 - 这是我们在钱包中给这个账户的名字。我们称之为测试：

```bash
> ethkey new test
```

输入一个密码来保护这个帐户(或者没有使用主密码)。
它会提示你输入一个密码来保护这个密钥。
如果您只按回车，它将使用默认的主密码。
通常这意味着当您想使用该帐户时(因为它记住主密码)，您不需要输入密钥的密码。
一般来说，您应该尝试为每个密钥使用不同的密码，因为它可以防止一个受损的密码访问其他帐户。
但是，出于方便，您可能会认为低安全性帐户使用相同的密码短语。

在这里，让我们给它123的令人难以置信的想象力密码。
(永远不要使用这样的简单密码来进行其他任何事情而不是短暂的测试账户)。
一旦你输入密码，它会要求你再次输入确认。
第二次输入123。
因为您给了它自己的密码短语，它还会要求您提供此密码的提示，只要它要求您输入该密码就会显示给您。
该提示存储在钱包中，并且本身受主密码的保护。
输入321倒退的真正可怕的暗示。

```bash
> ethkey new test

Enter a passphrase with which to secure this account (or nothing to use the master passphrase):
Please confirm the passphrase by entering it again:
Enter a hint to help you remember this passphrase: 321 backwards
Created key 055dde03-47ff-dded-8950-0fe39b1fa101
  Name: test
  Password hint: 321 backwards
  ICAP: XE472EVKU3CGMJF2YQ0J9RO1Y90BC0LDFZ
  Raw hex: 0092e965928626f8880629cec353d3fd7ca5974f
```

所有正常(又名直接)ICAP地址都以XE开头，所以您应该能够轻松识别它们。
还要注意，该键在创建键后有另一个标识符。
这就是所谓的UUID。
这是与帐户本身完全无关的密钥的唯一标识符。
知道它没有帮助攻击者发现你在网络上的人。
它也恰好是密钥的文件名，您可以在\〜/ .web3 / keys(Mac或Linux)或\ $ HOME / AppData / Web3 / keys(Windows)中找到该文件名。
现在让我们通过列出钱包中的密钥来确保它正常工作：

```bash
> ethkey list
055dde03-47ff-dded-8950-0fe39b1fa101 0092e965… XE472EVKU3CGMJF2YQ0J9RO1Y90BC0LDFZ  test
```

在这种情况下，我们的密钥存储在文件055dde中，并且具有从XE472EVK开始的ICAP地址....
在这种情况下，我们的密钥存储在文件055dde中，并且具有从XE472EVK开始的ICAP地址....
不是特别容易记住的东西，而是有用的，它也有它的专有名称，测试。

## 导入预售钱包

### 使用Mist以太坊钱包

使用GUI Mist Ethereum钱包导入预售钱包非常简单。
事实上，在安装应用程序的过程中，系统会询问您是否要导入预售钱包。

!!! Warning

    Mist钱包是beta软件。谨防和使用它需要您自担风险。

在创建帐户：使用Mist以太坊钱包<使用Mist - 以太坊钱包>一节中给出了安装Mist以太坊钱包的说明。

只需将您的`.json`预售钱包文件拖放到指定区域并输入您的密码即可导入您的预售帐户。

![presale-import](img/51PresaleImportInstall.png){.align-center width="436px" height="352px"}

如果您在安装应用程序时选择不导入预售钱包，可以随时通过选择应用程序菜单栏中的“帐户”菜单，然后选择“导入预售帐户”来导入它。

!!! Note

    Mist钱包仍在积极开发中，因此上述步骤的细节可能随升级而改变。

### 使用geth

如果您有geth的独立安装，则通过在终端中执行以下命令来导入预售钱包：

```bash
geth wallet import /path/to/my/presale-wallet.json
```

系统会提示您输入密码。

## 更新帐户

您可以将密钥文件升级到最新的密钥文件格式和/或升级密钥文件密码。

### 使用 geth

您可以使用带有帐户地址或索引作为参数的`update`子命令更新命令行上的现有帐户。
请记住，帐户索引反映了创建的顺序(包含创建时间的密钥文件名的字典顺序)。

```bash
geth account update b0047c606f3af7392e073ed13253f8f4710b08b6
```

要么

```bash
geth account update 2
```

例如：

```bash
$ geth account update a94f5374fce5edbc8e2a8697c15331677e6ebf0b

Unlocking account a94f5374fce5edbc8e2a8697c15331677e6ebf0b | Attempt 1/3
Passphrase:
0xa94f5374fce5edbc8e2a8697c15331677e6ebf0b
account 'a94f5374fce5edbc8e2a8697c15331677e6ebf0b' unlocked.
Please give a new password.
Do not forget this password.
Passphrase:
Repeat Passphrase:
0xa94f5374fce5edbc8e2a8697c15331677e6ebf0b
```

该帐户以加密格式保存在最新版本中，系统会提示您输入密码以解锁帐户，而另一个帐户则保存更新的文件。
可以使用相同的命令将不推荐格式的帐户迁移到最新的格式，也可以更改帐户的密码。

对于非交互式使用，可以使用`--password`标志指定密码：

```bash
geth --password <passwordfile> account update a94f5374fce5edbc8e2a8697c15331677e6ebf0bs
```

由于只能输入一个密码，所以只能进行格式更新，只能以交互方式更改密码。

!!! Note

    帐户更新具有可能会改变帐户顺序的副作用。
    成功更新后，该相同密钥的所有以前的格式/版本将被删除！

## 备份和恢复帐户

### 手动备份/恢复

您必须拥有帐户的密钥文件才能发送该帐户的任何交易。
密钥文件位于您以太坊节点数据目录的密钥库子目录中。
默认数据目录位置是平台特定的：

- Windows: `%appdata%\Ethereum\keystore`
- Linux: `~/.ethereum/keystore`
- Mac: `~/Library/Ethereum/keystore`

要备份您的密钥文件(帐户)，请复制`keystore`子目录中的个别密钥文件或复制整个`keystore`文件夹。

要恢复您的密钥文件(帐户)，请将密钥文件复制回原来位于的“keystore”子目录中。

### 导入未加密的私钥

`geth`支持导入未加密的私钥

```bash
geth account import /path/to/<keyfile>
```

该命令从纯文本文件`<keyfile>`中导入未加密的私钥，并创建一个新帐户并打印该地址。
假设密钥文件包含一个未加密的私钥，作为编码为十六进制的规范EC原始字节。
该帐户以加密格式保存，系统会提示您输入密码。
您必须记住此密码才能在未来解锁您的帐户。

一个数据目录被指定的例子。
如果不使用`--datadir`标志，则新帐户将被创建在默认数据目录中，即，密钥文件将被放置在数据目录的`keystore`子目录中。

```bash
$ geth --datadir /someOtherEthDataDir  account import ./key.prv
The new account will be encrypted with a passphrase.
Please enter a passphrase now.
Passphrase:
Repeat Passphrase:
Address: {7f444580bfef4b9bc7e14eb7fb2a029336b07c9d}
```

对于非交互式使用，可以使用`--password`标志指定密码：

```bash
geth --password <passwordfile> account import <keyfile>
```

!!! Note

    由于您可以直接将您的加密账户复制到另一个以太坊实例，所以当您在节点之间转账时，不需要此导入/导出机制。

!!! Warning

    当您将密钥复制到现有节点的`keystore`中时，您习惯使用的帐户顺序可能会发生变化。因此，请确保您不要依赖帐户顺序或仔细检查并更新脚本中使用的索引。
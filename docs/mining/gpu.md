# GPU挖矿

## 硬件

该算法内存很难，为了使DAG适合内存，每个GPU需要1-2GB的内存。如果你得到错误GPU挖掘。 ,GPU内存碎片？“你没有足够的内存。
GPU矿工在OpenCL中实现，所以AMD GPU将比同类NVIDIA GPU更“快”。ASIC和FPGA的效率相对较低，因此不鼓励。
要获得芯片组和平台的openCL，请尝试：

- [AMD SDK openCL](http://developer.amd.com/tools-and-sdks/opencl-zone/amd-accelerated-parallel-processing-app-sdk)
- [NVIDIA CUDA openCL](https://developer.nvidia.com/cuda-downloads)

## Ubuntu Linux 设置

对于这个快速指南，你需要Ubuntu 14.04或15.04和fglrx图形驱动程序。
您也可以使用NVidia驱动程序和其他平台，但您必须找到自己的方式来使用OpenCL进行安装，例如[Genoil的ethminer fork]（http://cryptomining-blog.com/tag/ ,ethminer /）。

如果您使用的是15.04版本，请转到“软件和更新>其他驱动程序”，并将其设置为“使用fglrx的AMD图形加速器的视频驱动程序”。

如果你使用的是14.04版本，请转到“软件和更新>其他驱动程序”，并将其设置为“使用来自fglrx的AMD图形加速器的视频驱动程序”。
不幸的是，对于你们中的一些人来说，由于Ubuntu 14.04.02中的一个已知错误，无法切换到GPU所需的专有图形驱动程序。

所以，如果你遇到这个错误，而且在你做其他事情之前，请转到“软件和更新>更新”，然后选择“提前发布的更新可靠”。
然后，返回到“软件和更新>其他驱动程序”，并将其设置为“使用fglrx的AMD图形加速器的视频驱动程序”）。
重新启动后，检查驱动程序是否已经正确安装（例如再次转到“其他驱动程序”）是非常值得的。

无论你做什么，如果你在04年4月14日，不要改变驱动程序或一旦设置的驱动程序配置。
例如，使用aticonfig --initial（尤其是使用-f，--force选项）可以“中断”您的设置。
如果你不小心改变了他们的配置，你需要卸载驱动程序，重新启动，重新安装驱动程序并重新启动。

## Mac 设置

```bash
wget http://developer.download.nvidia.com/compute/cuda/7_0/Prod/local_installers/cuda_7.0.29_mac.pkg
sudo installer -pkg ~/Desktop/cuda_7.0.29_mac.pkg -target /
brew update
brew tap ethereum/ethereum
brew reinstall cpp-ethereum --with-gpu-mining --devel --headless --build-from-source
```

你检查你的冷却状态：

```bash
aticonfig --adapter=0 --od-gettemperature
```

## Windows 设置

[下载最新的Eth ++安装]（https://github.com/ethereum-mining/ethminer/releases），并在安装屏幕的“选择组件”屏幕上选择ethminer

![image](img/eth_miner_setup.png)

## 与geth一起使用ethminer

```bash
geth account new // Set-up ethereum account if you do not have one
geth --rpc --rpccorsdomain localhost 2>> geth.log &
ethminer -G  // -G for GPU, -M for benchmark
tail -f geth.log
```

`ethminer`在端口8545（geth中的默认RPC端口）上与geth进行通信。
你可以通过给`geth`指定`--rpcport`选项来改变它。
Ethminer将在任何港口找到geth。
注意你需要用`--rpccorsdomain localhost`设置CORS头。
你也可以用`-F http：//127.0.0.1：3301`在`ethminer`上设置端口。
如果你想要在同一台计算机上挖掘多个实例，那么设置这些端口是必要的，尽管这有些没有意义。
如果您正在测试私有链，我们建议您使用CPU挖掘。

::: {.note}
::: {.admonition-title}
Note
:::

除非你想在GPU挖掘的TOP上进行CPU挖掘，否则你不需要给`geth`选项或者在控制台启动矿工。
:::

如果`ethminer`的默认值不起作用，请尝试使用`--opencl-device X`指定OpenCL设备，其中X是{0,1,2，...}。
当用`-M`（benchmark）运行`ethminer`时，你应该看到如下的东西：

```bash
Benchmarking on platform: { "platform": "NVIDIA CUDA", "device": "GeForce GTX 750 Ti", "version": "OpenCL 1.1 CUDA" }
Benchmarking on platform: { "platform": "Apple", "device": "Intel(R) Xeon(R) CPU E5-1620 v2 @ 3.70GHz", "version": "OpenCL 1.2 " }
```

调试`geth`：

```bash
geth  --rpccorsdomain "localhost" --verbosity 6 2>> geth.log
```

调试矿工：

```bash
make -DCMAKE_BUILD_TYPE=Debug -DETHASHCL=1 -DGUI=0
gdb --args ethminer -G -M
```

::: {.note}
::: {.admonition-title}
Note
:::

在GPU挖掘时，hashrate信息在`geth`中不可用

:::

用`ethminer`检查你的hashrate，`miner.hashrate`将总是报告0。

## 用ethminer和eth

### 在单个GPU上挖掘

为了在单个GPU上挖掘，所有需要完成的工作是使用以下参数来运行eth：

```bash
eth -v 1 -a 0xcadb3223d4eebcaa7b40ec5722967ced01cfc8f2 --client-name "OPTIONALNAMEHERE" -x 50 -m on -G
```

- `-v 1` 将详细程度设置为1.让我们不要被邮件垃圾邮件。
- `-a YOURWALLETADDRESS` 设置采矿奖励将会去的硬币库。,上面的地址只是一个例子。,这个论点是非常重要的，确保不要在你的钱包地址错误，否则你将不会得到以太付出。
- `--client-name "OPTIONAL"` 设置可选的客户端名称以在网络上识别您的身份
- `-x 50` 要求大量的同伴。,帮助在一开始找到同行。
- `-m on` 其实推出与采矿。
- `-G` 设置GPU挖掘。

当客户端运行时，您可以使用geth attach`或[ethconsole]（<https://github.com/ethereum/ethereum-console>）与它进行交互。

### 在多个GPU上挖掘

使用多GPU和eth进行挖掘与使用geth和多GPU进行挖掘非常相似。
确保正确运行您的coinbase地址的eth节点：

```bash
eth -v 1 -a 0xcadb3223d4eebcaa7b40ec5722967ced01cfc8f2 --client-name "OPTIONALNAMEHERE" -x 50 -j
```

请注意，我们还添加了-j参数，以便客户端可以启用JSON-RPC服务器与ethminer实例进行通信。
此外，我们删除了采矿相关的论点，因为乙胺将现在为我们做采矿。,对于您的每个GPU执行一个不同的乙胺实例：

```bash
ethminer --no-precompute -G --opencl-device X
```

其中X是您希望ethminer使用{0,1,2，...}的openCL设备对应的索引号。
为了轻松获得OpenCL设备列表，您可以执行`ethminer --list-devices`，它将提供OpenCL可以检测到的所有设备的列表，以及每个设备的一些附加信息。

Below is a sample output:

```console
[0] GeForce GTX 770
    CL_DEVICE_TYPE: GPU
    CL_DEVICE_GLOBAL_MEM_SIZE: 4286345216
    CL_DEVICE_MAX_MEM_ALLOC_SIZE: 1071586304
    CL_DEVICE_MAX_WORK_GROUP_SIZE: 1024
```

最后``无预计算'的论点要求乙方不要提前创建下一个时代的DAG。
虽然不建议这样做，因为每当出现时代转换时都会有采矿中断。

### 基准

采矿能力往往随着内存带宽的扩大而增长
我们的实现是用OpenCL编写的，而AMD的GPU通常比NVidia更能支持OpenCL。
经验证据表明，AMD的GPU在价格上比NVidia的产品有更好的挖掘性能。

要对单设备设置进行基准测试，您可以通过-M选项在基准测试模式下使用ethminer：

```bash
ethminer -G -M
```

如果你有很多设备，并且你想分别对每一个设备进行基准测试，你可以使用--opencl-device选项，类似于上一节：

```bash
ethminer -G -M --opencl-device X
```

使用ethminer`--list-devices`列出可能的数字来代替X {0,1,2，...}。

要开始在Windows上挖掘，首先[下载geth窗口二进制]（https://build.ethereum.org/builds/Windows%20Go%20master%20branch/）。

- 解压缩Geth（右键单击并选择解压缩）并启动命令提示符。使用cd导航到Geth数据文件夹的位置（例如，cd /转到C驱动器）
- 通过输入`geth --rpc`开始geth。

只要你输入这个，以太坊区块链将开始下载。
有时你的防火墙可能会阻止同步过程（这样做会提示你）。
如果是这种情况，请点击“允许访问”。

- 首先[下载并安装ethminer]（http://cryptomining-blog.com/tag/ethminer-cuda-download/），C ++挖掘软件（您的防火墙或Windows本身可能会执行，允许访问
- 打开另一个命令提示符（保留第一个命令提示符），通过键入cd / Program \ Files / Ethereum（++）/ release`来改变目录
- 现在确保geth已经完成同步区块链。,如果不再同步，可以通过在命令提示符下键入`ethminer -G`开始挖掘过程

此时可能会出现一些问题
如果出现错误，您可以通过按下`来中止矿工
如果错误提示“内存不足”，那么您的GPU没有足够的内存来挖掘以太网。
# 家园版文档倡议

[![Gitter](img/homestead-guide.svg)](https://gitter.im/ethereum/homestead-guide?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

## 目的和听众

This guide should serve to be an entry level for all Ethereum users and
developers. The goal is to create documentation with information, short
tutorials, and examples that will cover all of the basic and
intermediate functionality of using Ethereum to interact with dapps or
develop a dapp.

Any information that is overly specific, technical, or not necessary to
accomplish the documentation\'s goal will remain on the Ethereum Github
Wiki. It may be referenced in this guide if necessary.

Although much of the information will be similar between the Frontier
Guide and the Homestead Guide, efforts need to be made to make sure the
information ported over is still accurate. This document is client
agnostic, and examples and tutorials may be based on any client that the
author decides to write on, as long as a distinction is made as to what
client is being used in the examples/tutorials.

Although overly specific and technical documentation will not be
included in the first iterations of this guide, community use and
popularity of this guide will dictate future decisions to move Github
wiki documentation to this format.

过于具体和技术文件的例子包括：

- ETHash，CASPER，ABI，RLP或其他技术规格。
- 协议的完整API规范。 警告：如果一个例子， 报道, 或者教程需要引用客户端或接口的API调用以完成其示例，则可以引用特定的调用。 请务必在用户可以找到GitHub Wiki上的特定文档的其余部分时提供参考。

## 示范性文件资源

以下是以太坊文档的一些例子+文档的好例子。

- [固体文件](https://ethereum.github.io/solidity/docs/home)
- [边境指南](https://ethereum.gitbooks.io/frontier-guide/content)
- [Gav的TurboEthereum指南](https://gavofyork.gitbooks.io/turboethereum/content)
- [古代以太坊建造者指南](https://ethereumbuilders.gitbooks.io/guide/content/en/index.html)
- [其他以太坊链接](https://souptacular.gitbooks.io/ethereum-tutorials-and-tips-by-hudson/content/giant_ethereum_resource_list.html)
- [Django文档](https://docs.djangoproject.com/en/1.9)

## 重组文本标记, Sphinx

- [最好的备忘录](https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst)
- [快速参考](http://docutils.sourceforge.net/docs/user/rst/quickref.html)
- [官方备忘录](http://docutils.sourceforge.net/docs/user/rst/cheatsheet.txt) [html](http://docutils.sourceforge.net/docs/user/rst/cheatsheet.html)
- [RST 初级读本](http://sphinx-doc.org/rest.html)
- [sphinx文档](http://sphinx-doc.org/markup/inline.html)

## 编译和部署

我们使用make和自动生成的read-the-docs Makefile来构建文档。

```bash
git clone https://github.com/ethereum/homestead-guide
cd homestead-guide
make html
```

## 处理技巧

修正分隔符行（总是使用长度为80的长度为正确的长度，除非标题的长度大于80个字符）

```bash
for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\=+$/================================================================================/' > $f.o; mv $f.o $f; done; done
for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\*+$/********************************************************************************/' > $f.o; mv $f.o $f; done
for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\-+$/--------------------------------------------------------------------------------/' > $f.o; mv $f.o $f; done
for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\++$/++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++/' > $f.o; mv $f.o $f; done
for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\#+$/################################################################################/' > $f.o; mv $f.o $f; done
```

## 引用旧的文档

old-docs-for-reference文件夹包含Frontier Gitbook和Ethereum Wiki文档。 随意从这些仍然相关的文件复制/粘贴信息。

## 使用Pando迁移和转换旧Wiki内容

如果你仍然想克隆最新的以太坊Wiki和Frontier Guide文档：

```bash
git clone git@github.com:ethereum/go-ethereum.wiki.git
git clone git@github.com:ethereum/wiki.wiki.git

mkdir main-wiki.rst
mkdir go-ethereum-wiki.rst

for f in `ls wiki.wiki/*.md`; do pandoc $f -o main-wiki.rst/`basename $f .md`.rst; done
for f in `ls go-ethereum.wiki/*.md`; do pandoc $f -o go-ethereum-wiki.rst/`basename $f .md`.rst; done
```

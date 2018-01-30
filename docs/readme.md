# 家园版指南

[![License](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![Gitter](https://badges.gitter.im/ethereum/homestead-guide.svg)](https://gitter.im/ethereum/homestead-guide?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

The Ethereum Homestead Guide is the reference documentation accompanying
the Homestead release of the Ethereum project.

[Hosted on
ReadTheDocs](https://ethereum-homestead.readthedocs.org/en/latest/)

## 你可以帮助你

**Homestead Documentation Initiative**

It doesn't matter if you are a beginner or an expert, there are many
ways to help.

### 将内容写入指南

Help transfer and update content from the Ethereum Wiki, Ethereum
Frontier Guide, the Ethereum Stack Exchange, or any other reputable
source to relevant pages of the Homestead guide. Alternatively, write
your own content for the guide based on experience.

Make sure the documentation you are porting over is still accurate and
follows our guidelines for the Homestead docs
(<https://ethereum-homestead.readthedocs.org/en/latest/about.html>).

### 回顾已经写了什么

Have a look at our guide
(<https://ethereum-homestead.readthedocs.org/en/latest/>) and give us
feedback by visiting our Gitter Chatroom
(<https://gitter.im/ethereum/homestead-guide>) or submit a pull request
or issue to this repo. Too EZ.

### 这对我来说是什么？

Your name will forever be immortalized, both in my heart and on the
Contributors page in the guide. As a side effect, you may also get those
good feels that you get when you help improve documentation :-)

## 入门

This project uses Sphinx
(<http://www.sphinx-doc.org/en/stable/index.html>) to build html that is
published to Read the Docs. To run this documentation on your computer,
you should do the following:

### 先决条件

-   Python 2.6 or later
-   git

### 安装狮身人面像等

For OSX/Linux users (based on instructions here:
<https://read-the-docs.readthedocs.org/en/latest/getting_started.html>).
Sphinx as of 1.4.0 no longer automatically installs sphinx_rtd_theme,
hence its addition below.

-   From command line: `sudo pip install sphinx sphinx_rtd_theme`

For Windows users:

-   <http://www.sphinx-doc.org/en/stable/install.html#windows-install-python-and-sphinx>

### 获取源代码

-   git clone: <https://github.com/ethereum/homestead-guide.git>

### 构建和查看HTML

-   In a terminal window, go to your homestead-guide directory.
-   `make html`
-   `cd build/html`
-   `open index.html` (open in web browser)
-   Tip: each time you run `make html`, just reload your browser to view
    changes

## 资源

**家园**

-   Homestead Guide online:
    <https://ethereum-homestead.readthedocs.org/en/latest/index.html>
-   Github: <https://github.com/ethereum/homestead-guide>
-   Gitter: <https://gitter.im/ethereum/homestead-guide>
-   Google doc:
    <https://docs.google.com/document/d/1rVjrNgaDRAQdPp4rGqWrEk5fPgiHff0xsYGCyf06oM8/edit>

**旧版文档**

-   Ethereum Wiki: <https://github.com/ethereum/wiki/wiki>
-   Frontier Guide:
    <https://ethereum.gitbooks.io/frontier-guide/content/> (see below
    for converted files)
-   Souptacular's Giant List of Ethereum Resources:
    <https://souptacular.gitbooks.io/ethereum-tutorials-and-tips-by-hudson/content/giant_ethereum_resource_list.html>

**阅读文档和狮身人面像**

-   Read the Docs:
    <https://read-the-docs.readthedocs.org/en/latest/getting_started.html>
-   Sphinx docs: <http://www.sphinx-doc.org/en/stable/contents.html>
-   reStructuredText Primer:
    <http://www.sphinx-doc.org/en/stable/rest.html>
-   RST cheat sheet:
    <https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst>

## 目录结构

``` {.sourceCode .}
homestead-guide
  build    - workdir, not commited to repo
  source   - actual content in rst
    conf.py - sphinx configuration
  old-docs-for-reference (Frontier era stuff)
    wiki    - the legacy wiki
    gitbook - the legacy gitbook resources (converted to rst)
  make.bat - windows command to build docs
  Makefile - platforms with make to build docs
```

## 家园指南路线图（旧）

-   boilerplate using sphinx-quickstart
-   settings in conf.py
-   code up index with proposed structure
-   compile/deploy on readthedocs
-   include cheatsheat, rst/sphinx/readthedocs resources
-   reach out to community reddit - homestead documentation initiative
-   allocate chapters to people (ideally author and reviewer)
-   migrate old wiki under frontier/wiki (all md files converted to rst)
-   migrate old frontier-guide content under frontier/gitbook (all md
    content converted to rst)
-   script to annotate entire wiki with legacy warning

## 迁移老前辈指南内容的策略（旧）

-   temporaritly include resources about the documentation project
    within the book itself
    -   rst cheatsheet
    -   rst/sphinx/readthedocs resources
    -   compilation/deployment instructions
    -   link to issues and process
    -   style guide, conventions
-   include the rst conversion of the wiki
-   include the rst conversion of the gitbook

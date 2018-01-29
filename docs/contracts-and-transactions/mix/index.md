# Mix

IDE Mix旨在帮助您作为开发人员创建, 调试和部署契约和dapps（合约后端和前端）.

!!! warning "Warning"

    有很多关于OS X上Mix的崩溃引导问题的报告。
    这个问题是我们一直在追赶一两个月的[海森虫](https://en.wikipedia.org/wiki/Heisenbug)。
    我们现在最好的解决方法是使用调试配置, 像这样:

    ```bash
        cmake -DCMAKE_BUILD_TYPE=Debug ..
    ```

!!! warning "Warning"

    Mix的替代名为[Remix](https://blog.ethereum.org/2016/05/04/c-dev-update-announcing-remix/)正在进行，所以如果你使用Mix遇到问题，你可能会更好地寻找替代品，直到Remix更成熟。

首先创建一个由以下内容组成的新项目

- 合约
- html文件
- JavaScript文件
- 样式文件
- 图像文件
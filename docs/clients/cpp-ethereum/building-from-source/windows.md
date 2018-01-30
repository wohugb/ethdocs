# Windows构建

我们仅支持** 64位**版本，仅适用于以下版本的Windows：

-   [Windows 7](https://en.wikipedia.org/wiki/Windows_7)
-   [Windows 8/8.1](https://en.wikipedia.org/wiki/Windows_8)
-   [Windows 10](https://en.wikipedia.org/wiki/Windows_10)
-   [Windows Server 2012     R2](https://en.wikipedia.org/wiki/Windows_Server_2012_R2)

It may be possible to get the client working for Windows 32-bit, by disabling EVMJIT and maybe other features too. We might accept pull-requests to add such support, but we will not put any of our own development time into supporting Windows 32-bit builds.

## 先决条件

You will need to install the following dependencies

  ---------------------------------------------------------------------------------------------------------------------
  Software                                                                Notes
  ----------------------------------------------------------------------- ---------------------------------------------
  [Git for Windows](https://git-scm.com/download/win)                     Command-line tool for retrieving source from
                                                                          Github.

  [CMake](https://cmake.org/download/)                                    Cross-platform build file generator.

  [Visual Studio                                                          C++ compiler and dev environment.
  2015](https://www.visualstudio.com/products/vs-2015-product-editions)
  ---------------------------------------------------------------------------------------------------------------------

## 获取源代码

Clone the git repository containing all the source code by executing the
following command: :

    git clone --recursive https://github.com/ethereum/cpp-ethereum.git
    cd cpp-ethereum

## 获取外部依赖关系

Execute the CMake script that downloads and unpacks pre-built external libraries needed to build the project: :

    scripts\install_deps.bat

## 生成Visual Studio项目文件

Then execute the following commands, which will generate a Visual Studio solution file using CMake: :

    mkdir build
    cd build
    cmake -G "Visual Studio 14 2015 Win64" ..

Which should result in the creation of **cpp-ethereum.sln** in that build directory.

**NOTE: We only support Visual Studio 2015 as of cpp-ethereum-v.1.3.0.
If you don\'t have it already, install the [Visual C++ 2015 Build
Tools](http://landinghub.visualstudio.com/visual-cpp-build-tools)**

Double-clicking on that file should result in Visual Studio firing up. We suggest building **RelWithDebugInfo** configuration, but all others work.

## 建立在命令行上

Alternatively, you can build the project on the command-line, like so: :

    cmake --build . --config RelWithDebInfo

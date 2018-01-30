# Linux构建

## 获取源代码

我们使用git和GitHub来维护源代码,通过以下方法克隆存储库：

```bash
git clone --recursive https://github.com/ethereum/cpp-ethereum.git
cd cpp-ethereum
```

The `--recursive` option is important. It orders git to clone additional submodules which are required to build the project. If you missed it you can correct your mistake with command `git submodule update --init`.

## CMake

We use CMake to control the build configuration of the project. Quite recent version of CMake is required (at the time of writing 3.4 is the minimum). We recommend installing CMake by downloading and unpacking the binary distribution of the latest version available on the download page:

<https://cmake.org/download/>

> **Alternative method**
>
> The repository contains the script
> [install\_cmake.sh](https://github.com/ethereum/cpp-ethereum/blob/develop/scripts/install_cmake.sh)
> that downloads a fixed version of CMake and unpacks it to the given
> directory prefix. Example usage
> `scripts/install_cmake.sh --prefix /usr/local`.

## 安装依赖关系

The following *libraries* are required to be installed in the system:

- boost
- leveldb
- curl
- microhttpd
- miniupnp
- gmp

They usually can be installed using distribution-specific package
manager. For example on Debian-based systems:

    sudo apt-get install libboost-all-dev libleveldb-dev libcurl4-openssl-dev libmicrohttpd-dev libminiupnpc-dev libgmp-dev

or on RedHat-based systems:

    dnf install boost-devel leveldb-devel curl-devel libmicrohttpd-devel miniupnpc-devel gmp-devel

Linux has a horror-show of fragmentation when it comes to packaging
systems.

We support a [\"one-button\" bash script](https://github.com/ethereum/cpp-ethereum/blob/develop/scripts/install_deps.sh) which attempts to make this minefield more navigable for users of common distros. It identifies your distro and installs the external packages which you will need, using whatever combination of package servers and build-from-source is required for your specific distro version. This is a non-trivial task, but by that token is also something which we don\'t want anybody to have to replicate themselves.

```bash
scripts/install_deps.sh
```

We use the same script for automated builds and continuous integration, so it is continuously tested, which is especially important on MacOS, where Homebrew is a constantly moving target.

If you try it, and it doesn\'t work for you, please [report the problem](https://github.com/ethereum/cpp-ethereum/issues/new) with details of your distro, your version number and any other important details and we can work together to get it working for your use-case. We have manual instructions for Fedora, openSUSE and Arch Linux (see below). If you using some other distro then please contact us and we\'ll see if we can get you going.

::: {.toctree}
linux-fedora.rst linux-opensuse.rst linux-arch.rst
:::

## 建立在命令行上

When you have installed your dependencies you can build.

```bash
mkdir build                                              Make a directory for the build output
cd build                                                 Switch into that directory

cmake ..                                                 To generate a makefile.
make                                                     To build that makefile on the command-line
make -j<number>                                          (or) Execute makefile with multiple cores in parallel
```

## 32位的Linux版本

We have cpp-ethereum building and running successfully on many 32-bit Linux distros, with the main constraint being the availability of external dependencies in 32-bit variants. Probably the most active demand here is for single-board computers like the Raspberry Pi family.

You will need to disable the JIT and the heavy-weight LLVM dependency which comes with that. EVMJIT only supports x86\_64. Other than that, cpp-ethereum should \"just work\" on 32-bit platforms. To disable JIT, you will need to use the following command for the Makefile generation phase:

```bash
cmake .. -DEVMJIT=Off
```

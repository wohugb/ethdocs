Connecting to Ethereum Clients {#Connecting to Clients}
==============================

Ethereum clients expose a number of methods over
[JSON-RPC](https://github.com/ethereum/wiki/wiki/JSON-RPC) for
interacting with them from within an application. However, interacting
directly over JSON-RPC passes on a number of burdens to the application
developers, such as:

> -   JSON-RPC protocol implementation
> -   Binary format encoding/decoding for creating and interacting with
>     smart contracts
> -   256 bit numeric types
> -   Admin command support - e.g. create/manage addresses, sign
>     transactions

A number of libraries have been written to help address these issues,
allowing application developers to focus on their applications, instead
of the underlying plumbing to interact with Ethereum clients and the
wider ecosystem.

  -------------------------------------------------------------------------------------------
  Library                       Language     Project Page
  ----------------------------- ------------ ------------------------------------------------
  [web3.js]{role="ref"}         JavaScript   <https://github.com/ethereum/web3.js>

  [web3j]{role="ref"}           Java         <https://github.com/web3j/web3j>

  [Nethereum]{role="ref"}       C\# .NET     <https://github.com/Nethereum/Nethereum>

  [ethereum-ruby]{role="ref"}   Ruby         <https://github.com/DigixGlobal/ethereum-ruby>

  [web3.py]{role="ref"}         Python       <https://github.com/ethereum/web3.py>
  -------------------------------------------------------------------------------------------

Information on each library is provided in the following sections:

::: {.toctree}
web3.js/index.rst web3j/index.rst nethereum/index.rst
ethereum-ruby/index.rst web3.py/index.rst
:::

For an overview of creating and interacting with smart contracts and
transactions via the web3.js library, please refer to the section
[Accessing Contracts and Transactions]{role="ref"}.

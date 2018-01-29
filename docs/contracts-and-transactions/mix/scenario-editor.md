# 方案编辑

方案可以用来测试和调试合同。

A scenario is effectively a local blockchain where blocks can be mined
without PoW -- otherwise testing would be quite slow ;).

A scenario consists of a sequence of transactions. Usually, a scenario
would start with the contract creation scenarios of the dapp. In
addition, further transactions can be added to test and debug the dapp.
Scenarios can be modified, i.e. transactions can be removed. Note that a
scenario needs to be rebuilt for modifications to become effective.
Further testing can be done using local JS calls via the JS API.

In case it's not open, access the scenario and debugger pane by pressing
F7 or Windows \> Show right or the debug button in the upper right
corner of the main window.

## 创建和设置一个新的方案

When you launch Mix for the first time, an empty scenario, i.e. not
containing any transactions, will be created. Add an account named
"MyAccount" and set it's initial balance to 1 ether. Click OK. Rename
the scenario to "Deploy".

## 修改帐户的初始以太平衡

Actually, we want to do a lot of tests Edit the Genesis block parameters
and set your initial account balance to 1000 ether. Rebuild the scenario
for the change to become effective.

## 重建场景

Each time a transaction is modified or an account added, the scenario
has to be rebuilt for modifications to become effective. Note that if a
scenario is rebuilt the web frontend (local storage) may also need to be
reset (this is not done automatically be Mix).

## 创建一个事务

Let's get some ether sent to Bob. Create another account named "Bob"
with zero ether balance. Create a new transaction in the scenario pane.
Click "Add Tx..." and send 300 ether to Bob. Add a block.

## 改变和重复使用场景

Create a new scenario or start from a scenario with several transactions
that you duplicate first

Rename the scenario

Modify scenario by specifying transactions that shall be removed

Rebuild the scenario

## 显示呼叫

A contract call is a function invokation. This is not a transaction as a
contract call cannot change the state. A contract call is not part of
the blockchain but for practical and ux design reason, it is convenient
to display calls at the same functional level as a transaction. The JS
icon warn you that this is not a transaction but a call. To show/hide
call, click on the menu Scenario -\> Display calls.

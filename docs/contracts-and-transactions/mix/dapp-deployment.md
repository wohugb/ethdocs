# Dapps部署

| This feature allows users to deploy the current project as a Dapp in
  the main blockchain.
| This will deploy contracts and register frontend resources.

The deployment process includes three steps:

- | **部署合同**:
  | This step will deploy contracts in the main blockchain.

- | **打包dapp**:
  | This step is used to package and upload frontend resources.

- | **注册**:
  | To render the Dapp, the Ethereum browser (Mist or AlethZero) needs
    to access this package. This step will register the URL where the
    resources are stored.

To Deploy your Dapp, Please follow these instructions:

| Click on `Deploy`, `Deploy to Network`.
| This modal dialog displays three parts (see above):

- **部署合同**
- *选择方案*

"Ethereum node URL" is the location where a node is running, there must
be a node running in order to initiate deployment.

"Pick Scenario to deploy" is a mandatory step. Mix will execute
transactions that are in the selected scenario (all transactions except
transactions that are not related to contract creation or contract
call). Mix will display all the transactions in the panel below with all
associated input parameters.

"Gas Used": depending on the selected scenario, Mix will display the
total gas used.

- *部署场景*

"Deployment account" allow selecting the account that Mix will use to
execute transactions.

"Gas Price" shows the default gas price of the network. You can also
specify a different value.

"Deployment cost": depending on the value of the gas price that you want
to use and the selected scenario. this will display the amount ether
that the deployment need.

"Deployed Contract": before any deployment this part is empty. This will
be filled once the deployment is finished by all contract addresses that
have been created.

"Verifications". This will shows the number of verifications (number of
blocks generated on top of the last block which contains the last
deployed transactions). Mix keep track of all the transactions. If one
is missing (unvalidated) it will be displayed in this panel.

- *打包dapp*

The action "Generate Package" will create a new folder named \'www\',
this folder will contain all the resources and scripts will be mapped to
the current deployed contract. In order to publish your dapp, you need
to host the www folder in a webserver (to be replace soon by IPFS and
SWARM). by default the library web3.js is not included. If you want to
be able to use the dapp in a standard web browser, you wiil need to
include this library.

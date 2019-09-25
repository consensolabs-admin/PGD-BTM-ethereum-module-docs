---
description: Introduction to basics of decentralized application development
---

# DApp development

## Communicating with Ethereum nodes and smart contract

One of the crucial aspects of decentralized application is **user experience**. Every user of the DApp should seamlessly establish a direct communication with the Ethereum node and interact with the the deployed smart contract by forwarding the signed transactions.

Ethereum node/ client provides interface for communication with the help of JSON-RPC protocol. User can make JSON-RPC requests over HTTP, WebSocket or IPC. 

## Libraries and tools

Ethereum provides several tools and libraries to conveniently interact with the remote nodes.

### [Remix](https://remix.ethereum.org)

Remix is a web IDE with built in static analysis. It supports compiling, testing, debugging and deploying of smart contracts and much more straight from the client browser.

### Web3.js

Web.js is JavaScript package with a collection of libraries which allow you to interact with a local or remote Ethereum node.

```text
Web3 = require('web3')
web3 = new Web3(new
Web3.providers.HttpProvider("http://localhost:8545"));
web3.eth.getBlockNumber(console.log);

```

### [MetaMask](https://metamask.io/)

![MetaMask Bridge \(https://metamask.io\)](.gitbook/assets/ethereum-metamask-chrome.png)

MetaMask is a browser extension that acts as a bridge between the client application and the Ethereum node. It allows to connect with the Ethereum mainnet, testnet \(Ropsten, Koban, Rinkeby and Goerli\) nodes without running their clients locally.

It also comes with a secure wallet that lets user manage multiple accounts and sign the transaction while interacting with the node.

### [Ganache](https://www.trufflesuite.com/ganache) 

A personal local blockchain for development purpose that can emulate most of the behavior of Ethereum network. 

{% hint style="danger" %}
Although **Ganache** helps to test the DApps locally, it is always advised to run the DApp on testnet before deploying it to the mainnet.
{% endhint %}

Ganache can be installed just as a CLI application and as a [desktop application.](https://www.trufflesuite.com/ganache) CLI application can be installed using NPM:

```text
$ sudo npm install ganache-cli -g 
```

### Creating a basic DApp \(TODO list\)

#### Smart contract

`Task` structure

```text
struct Task {
  uint id;
  string content;
  bool completed;
}
```

`TaskCreated` event

```text
// CREATE TaskCreated event
event TaskCreated(
  uint id,
  string content,
  bool completed
);

```

`TaskToggled` event

```text
event TaskToggled(
  uint id,
  bool completed
);
```

`CreateTask` function

```text
taskCount ++;
tasks[taskCount] = Task(taskCount, _content, false);
emit TaskCreated(taskCount, _content, false);
```

`toggleTask` function

```text
Task memory _task = tasks[_id];
_task.completed = !_task.completed;
tasks[_id] = _task;
emit TaskCompleted(_id, _task.completed);
```

**1.Start a private blockchain \(Ganache\).**

```text
 $ ganache-cli --seed amityonline
```

#### 2.  Deploy the contract

1. Open [https://remix.ethereum.org](https://remix.ethereum.org/)
2. Paste the Solidity contract code
3. Compile and deploy the contract to the local blockchain
4. Note down the deployed contract address and update it in the front end application

#### 3. Run the front end React application

```text
 $ cd dapp-development/todo-list/
 $ npm start
```

#### 








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



### Creating a basic DApp \(TODO list\)


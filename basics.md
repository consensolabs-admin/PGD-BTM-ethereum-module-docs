---
description: 'Basic concepts of Ethereum blockchain, client and network'
---

# Ethereum Basics

## Ether currency

Ether \(ETH or Ξ\) is the native cryptocurrency used on the Ethereum network and is used to compensate miners who secure transactions. It could be used as:

* Store of value \(e.g. in lending collateral\)
* A medium of exchange \(e.g. in trade and payments\)

## Types of accounts

## Wallets

In its basic sense, wallet is something manages keys and addresses , tracks and transacts user's money.

But most of the Ethereum wallets are capable fully interacting with smart contracts and Ethereum nodes.

* Ledger Nano S \(Hardware wallet\)
* MetaMask \(Web wallet + DApp Bridge \)
* [MyEtherWallet](https://www.myetherwallet.com/) \(Web + Mobile wallet\)
* TrustWallet \(Mobile wallet\)

## Transactions

These are signed messages originated by externally owned account and transmitted to the Ethereum network  and finally recorded on the blockchain.

{% hint style="info" %}
Transactions are the only thing responsible to change the state and execute the smart contracts.
{% endhint %}



![Transaction structure](.gitbook/assets/amity-transactions.png)

## Smart contracts

Smart contract is an program that is deployed to the Ethereum blockchain and whose functions could be triggered by external users so that it can be executed on Ethereum virtual machines \(EVM\)

{% page-ref page="smart-contracts.md" %}

## GAS

GAS is fuel for the transactions in Ethereum. It controls the amount of resources that a transaction can use. 

Gas is not equal to Ether. Value of each Gas unit is represented by **gasPrice**. Higher the gasPrice higher the chances of getting included in the block.

{% hint style="info" %}
gasPrice is measured in gwei. 

* 1 ETH = 10^9 gwei
* 1 gwei = 1 billion wei
{% endhint %}

The amount of gas units required for each transaction is represented as **gasLimit**. A simple transfer ETH transaction required 21,000 gas units.

## Blockchain and explorers

## EVM



## Ethereum clients

## Ethereum networks

### Mainnet and testnets

### Working with the private network

## 


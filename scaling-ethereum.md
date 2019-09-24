---
description: Scaling solutions in Ethereum blockchain
---

# Scaling Ethereum

Just like Bitcoin or any other public blockchain, Ethereum also suffers from limited scalability of the transactions. Ethereum mainly suffers due to two reasons:

1.  Proof-of-work consensus algorithm which has higher finality \(settlement \) time.
2. High GAS cost for each smart contract interaction.

There are two layer 2 solutions to solve the scalability issue of Ethereum network - **State channels** and **Side chains**.

## State channels 

### Raiden Network

## Sidechains 

Side chain is a separate chain that is attached to the main chain using two way peg. The side chain mechanism allows asset to be moved between the chains by locking and unlocking those assets.

The sidechain depends on a different consensus mechanism. Consensus algorithms that can achieve the faster transaction finality such as PoA are often preferred. 

### [Loom network](https://loomx.io/developers/en/intro-to-loom.html):

Loom network is the most advanced scaling solution available in production. It helps to scale Ethereum by running a custom blockchan. It has a chain called PlasmaChain that acts as a bridge between several other major blockchains. 

### [Matic network](https://docs.matic.network/):

Matic Network is another  sidechain based scaling solution for public blockchains. It is based on an adapted implementation of Plasma framework.

The existing smart contract can be deployed directly to the Matic side chain without any setup.

{% hint style="info" %}
Matic testnet RPC url: `https://testnet2.matic.network`
{% endhint %}

## Ethereum 2.0


---
description: Advanced implementation with frameworks
---

# Advanced Development

## Tools and frameworks

### Truffle

Truffle is development environment, deployment, testing framework for Ethereum blockchain.

* Built-in smart contract compilation, deployment
* Automated contract testing with Mocha and Chai.
* Scriptable deployment & migrations framework.
* Network management for deploying to many public & private networks.
* Interactive console for direct contract communication.
* Instant rebuilding of assets during development.
* External script runner that executes scripts within a Truffle environment.

Truffle can be installed as a node module.

```text
$ npm install -g truffle
```

Quick start

```text
$ truffle init
```

### Few other frameworks

* [Embark](https://github.com/embark-framework/embark) - Framework for DApp development
* [Dapp](https://dapp.tools/dapp/) - Framework for DApp development, successor to DApple
* \*\*\*\*[Drizzle](https://www.trufflesuite.com/drizzle)**:** Collection of front-end libraries for seamless DApp development 
* [Brownie](https://github.com/HyperLink-Technology/brownie) - A python framework for testing, deploying and interacting with Ethereum smart contracts.

### Truffle boxes

[Truffle Boxes](https://www.trufflesuite.com/boxes) are helpful boilerplates that allow you to focus on what makes your DApp unique.

Quick start

```text
$ truffle unbox react
```

### Open Zeppelin

[OpenZeppelin](https://docs.openzeppelin.com/openzeppelin/) allows to create secure smart contracts by following a set of standards. They mainly provide:

* **Contracts** - Set of secure reusable contracts
* **SDK**: Set of tools to develop, test and deploy contracts
* **Starter kits**: Bundles to kick start DApp development

### Ganache 

A personal local blockchain for development purpose that can emulate most of the behavior of Ethereum network. 

## [ERC721](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md) based Crypto collectible

> The “token” is just an entry in the token contract, and who “owns” a token is recorded in the contract. A token is never in “your” wallet

**ERC-20:** is a standard that describes the basic functionalities of a fungible token.

**ERC-721** is a free, open standard that describes how to build non-fungible or unique tokens on the Ethereum blockchain 

Examples: [OpenSea](https://opensea.io/), [CryptoKitties](https://www.cryptokitties.co)

![https://www.cryptokitties.co](.gitbook/assets/kitties.png)

{% hint style="info" %}
* ERC-20: For money and money-like tokens.
* ERC-721: For things and thing-like tokens
{% endhint %}

## Smart contract

Import `ERC721Full`

```text
import 'openzeppelin-solidity/contracts/token/ERC721/ERC721Full.sol';
```



Inherit the `ERC721Full`

```text
contract Color is ERC721Full {
constructor() ERC721Full("Color", "COLOR") public {
  }
```

`mint` Function

```text
require(!_colorExists[_color]);
uint _id = colors.push(_color);
_mint(msg.sender, _id);
_colorExists[_color] = true;
```

#### Compile, deploy and test the contract

```text
 $ truffle migrate --network development
```

Mocha testing



```text
describe('deployment', async () => {
  it('deploys successfully', async () => {
    const address = contract.address
    assert.notEqual(address, 0x0)
    assert.notEqual(address, '')
    assert.notEqual(address, null)
    assert.notEqual(address, undefined)
  })

  it('has a name', async () => {
    const name = await contract.name()
    assert.equal(name, 'Color')
  })

  it('has a symbol', async () => {
    const symbol = await contract.symbol()
    assert.equal(symbol, 'COLOR')
  })

})

describe('minting', async () => {

  it('creates a new token', async () => {
    const result = await contract.mint('#EC058E')
    const totalSupply = await contract.totalSupply()
    // SUCCESS
    assert.equal(totalSupply, 1)
    const event = result.logs[0].args
    assert.equal(event.tokenId.toNumber(), 1, 'id is correct')
    assert.equal(event.from, '0x0000000000000000000000000000000000000000', 'from is correct')
    assert.equal(event.to, accounts[0], 'to is correct')

    // FAILURE: cannot mint same color twice
    await contract.mint('#EC058E').should.be.rejected;
  })
})

describe('indexing', async () => {
  it('lists colors', async () => {
    // Mint 3 more tokens
    await contract.mint('#5386E4')
    await contract.mint('#FFFFFF')
    await contract.mint('#000000')
    const totalSupply = await contract.totalSupply()

    let color
    let result = []

    for (var i = 1; i <= totalSupply; i++) {
      color = await contract.colors(i - 1)
      result.push(color)
    }

    let expected = ['#EC058E', '#5386E4', '#FFFFFF', '#000000']
    assert.equal(result.join(','), expected.join(','))
  })
})
```

```text
$ truffle test
```



### Client application \(Truffle + React + Web3.js + MetaMask\) 

`loadBlockchainData` function

```text
const web3 = this.web3;
const accounts = await web3.eth.getAccounts();
this.setState({ account: accounts[0] });

const networkId = await web3.eth.net.getId();
const networkData = Color.networks[networkId];
if(networkData) {
  const abi = Color.abi;
  const address = networkData.address;
  this.contract = new web3.eth.Contract(abi, address);
  await this.loadColorTokens();
} else {
  window.alert('Smart contract not deployed to detected network.')
}
```



`loadColorTokens` function

```text
const totalSupply = await this.contract.methods.totalSupply().call();
this.setState({ totalSupply });

for (var i = 1; i <= totalSupply; i++) {
    const color = await this.contract.methods.colors(i - 1).call();
    this.setState({
        colors: [...this.state.colors, color]
    })
}
```



`mint` function

```text
this.contract.methods.mint(color).send({ from: this.state.account })
.on('transactionHash', (receipt) => {
    console.log('created');
  this.setState({
    colors: [...this.state.colors, color]
  })
})
```

**1.Start a private blockchain \(Ganache\).**

```text
 $ ganache-cli --seed amityonline
```

#### 

#### 2. Run the front end React application

```text
 $ cd advanced-development/color-token/
 $ npm install
 $ npm start
```






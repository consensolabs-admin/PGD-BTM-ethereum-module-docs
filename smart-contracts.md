---
description: Introduction to smart contracts and Solidity programming
---

# Smart Contracts

> “A smart contract is a set of promises, specified in digital form, including protocols within which the parties perform on these promises.” - Building Blocks for Digital Markets
>
>  **- Nick Szabo**

Smart contract in context of distributed ledger is all about making the script more intelligent. Smart contract when deployed in a decentralized network  allows it to be verified and enforced in a self-executing manner and removes any third party arbitrator.

Ethereum allows intelligent script to be deployed and executed in the network. Ethereum achieves this with the help of virtual machine \(EVM\) and high level scripting languages such as Solidity.

{% hint style="info" %}
The term "_smart contract_" is sometimes misleading because Ethereum script is not limited to execute just simple contracts. A more suitable name would be "**immutable executable script**"
{% endhint %}

## Smart contract life cycle

* Contract is created with a special contract creation transaction
* Contract can call other contracts
* Contract updates the global state only if execution is successful
* Contract can also be destroyed with a special instruction \(SELFDESTRUCT\)

## Smart contract languages

Ethereum smart contract languages are high level imperative programming language that compiles to EVM bytecode. Since Ethereum smart contract is turing complete, it will provide most of the constructs that are present in the general purpose programming language,

Ex: Serpant, Vyper\(syntax similar to Python\), Bamboo, Solidity 

## Solidity

Solidity is the popular and widely used contract language for DApp development. ****It is a contract-oriented programming language influenced by C++, Python and JavaScript

### Compiling the contract \(Solc\)

Solidity programs can be compiled in several ways using several tools. `solc` is the basic compiler developed by Ethereum community. It can be installed in [several ways](https://solidity.readthedocs.io/en/v0.5.11/installing-solidity.html).

Most of the tools will use a JavaScript version of the compiler called `solc-js`. Remix IDE is the preferred way to compile and deploy the smart contract for beginners.

```text
solc --bin Greetings.sol
```

### Application binary interface \(ABI\)

ABI is crucial to communicate to interact with the deployed smart contract. ABI is created while compiling the contract and defines an interface to interact with the compiled byte code.

{% hint style="info" %}
**Ethereum’s ABI is specified as JSON array of function and event descriptions**
{% endhint %}

```text
solc --abi Greetings.sol
```



### GAS consideration

### Programming with Solidity

Structure of the solidity contract is similar to classes in object oriented languages. Just like general purpose programs Solidity contract can have _variables_, _functions_, _datatypes_ such as _struct_, _enum_. Further, contracts can _inherit_ other contracts and _implement_ inter

#### Visibility: 

 `public` : Can be accessed from anywhere \(contract or EOA\)

`external`: Cab be accessed from EOA 

`internal` : Can be accessed from within the contract \(including derived contract\)

 `private`: Can be accessed only with the contract

#### [Data types](https://solidity.readthedocs.io/en/v0.5.11/types.html)

Each variable in Solidity needs to be defined with data type since Solidity is statically typed.

#### Value types:

**Boolean:**  true or false.

**Integers**: Has both signed \(`int8` to `int256`\) and unsigned \(`uint8` to `uint256`\).

**Address**: 20-byte or 40-character hexadecimal Ethereum address \(`0xEBE41EC4C574FDE7A1D13d333d17267ca93DF491`\).

**Byte array**: Fixed \(`bytes1` to `bytes32`\) and dynamic \(`bytes` and `string`\)

#### Reference types:

Reference type data structure such as array and struct need addition data location information. Data location can be **memory**, **storage** or **calldata.**

**Arrays:** Arrays can be fixed or dynamic. 

```text
uint[] memory ids;
bytes[] storage names;

```

**Struct:** 

```text
struct User {
  uint id;
  address addr;
  string name;
  }
  
User memory user;

```



**Mapping:**  Maps a key to value just like hashmap. Syntax: `mapping(_KeyType => _ValueType)`



#### Contract definition

```text
pragma solidity >=0.4.0 <0.7.0;

contract Greetings {
    // ...
}
```

#### Functions

Functions can take any number of inputs and return any number of outputs.

```text
    function add(uint _a, uint _b)
        public
        pure
        returns (uint o_sum)
    {
        o_sum = _a + _b;
    }

```

#### View function

Function that doesn't modify the state of the contract

* Will not write to state variables
* Will not emit events
* Will not create other events
* Will not use`selfdestruct`.
* Will not send Ether via calls.
* Will not call any function not marked `view` or `pure`.
* Will not use low-level calls.
* Will not use inline assembly that contains certain opcodes.

```text
string public owner;

function getOwner() public view returns (string) {
  return owner;
}
```

#### Pure function

Function that doesn't read or modify the state

#### Fallback function

Fallback function  is an unnamed function that will be executed if none of the function match the function call.

```text
contract Payment {

    function() external payable {
    // Transfer Ether
   }
}
```

#### Constructors

Special function named constructor is called only once during the contract creation. Often used to update the state of the contract to some default values during the contract deployment.

```text
constructor() public {
    // Constuct Something
    }
```

#### Self destruct 

A contract can only be deleted by explicitly calling a high level built in function called selfdestruct. This command must be present in the contract to make it deletable.

 It takes an address as an argument to which the contract balance will be sent to.

```text
function destroy() public {
    require(msg.sender == owner);
    selfdestruct(address recipient) 
}
```

#### Modifiers

It is a special type of function that modifies the behavior of other function. Modifier name is added to the function declaration.

```text
modifier onlyOwner {
    require(msg.sender == owner);
}

function destroy() public onlyOwner {
    selfdestruct(owner);
}
```

####  Inheritance

Supports inheritance to extend a contract with additional functionality.

```text
contract Child is Parent {
...
}
```

####  Events

These are used to send transaction receipts to the invoker. Events are defined with `event` keyword and called with `emit` keyword.

#### Error handling

`Assert` and `require` evaluates the condition and halts the execution if the condition is false.

```text
require(msg.sender == owner);
```

 `Revert` function intentionally halts the contract execution.

#### 

#### Sample contract

```text
pragma solidity ^0.5.0;

contract Greetings {
    
    string public owner;

    constructor(string memory name) public {
      owner = name;
    }
    
    function greetUser() view public returns (string memory) {

        return string(abi.encodePacked("Greetings from  ",owner));
  }
}
```


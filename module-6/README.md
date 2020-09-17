# Smart contract fundamentals in solidity

## Data types & variables 
- Statically typed
- Compiled lang
- Elem types 
- Complex types 
- Mappings

# Functions in solidity
```
function <function name>(<params>) 
    [internal | external | public | private]
    [ pure | constant | view | payable] 
    [modifiers]
    [returns(<returns types>)] {
        <body>
    }
```

## For return type, there are 2 manners to write it
1.
```
string name = AemieJ;
function some() returns (string) {
    return name;
}
```

2.
```
string name = AemieJ;
function some() returns (string _name) {
    _name = name;
}
```

## Pure functions 
- Reading from state variables 
- Accessing balance 
- Accessing any of the members of block, tx, msg 
- Calling any func not marked pure 
- modify input to give o/p

## Payable functions
- Functions that handle the error 

## Throwing exceptions 
You can throw it with: 
- assert() 
- require() 
- revert(): always throws an exception

## Function modifiers 
- can be defined with keyword modifier 

```
string name;
address owner;

modifier onlyOwner {
    require(msg.sender == owner);
    _;
}

function setName(string _name) onlyOwner {
    name = _name;
}
```
## Callback functions 
> limited to gas (2300) 

Contracts can have only one unnamed function (takes no argument and returns nothing as well)
```
uint balance; 

function () public payable {
    balance += msg.value;
}
```

# Storage & Memory
### Storage 
- Persistent across executions 
- expensive to use 
- are written to every blockchain and stored in every node 

### Memory
- sticks for the duration of function call
- cheap to use 

### Call stack 
- cheapest, almost free to use 
- focused on local variables 

### Note
- State variables: storage 
- Function arguments: memory
- Structs, array and memory are passed by reference 

Reference link to this is [here](https://solidity.readthedocs.io/en/v0.4.21/introduction-to-smart-contracts.html#storage-memory-and-the-stack)

# Contract Structure
1. First is the `pragma` statement to include the specific version of solidity.

2. Contract initializer `contract ContractName {}`
3. Specify the variables within contracts
4. Specify the events
5. Specify the function modifiers
6. Specify the functions > declare the constructor first
> Possible to write inline assembly code within smart contracts 

Reference is [here](https://solidity.readthedocs.io/en/develop/structure-of-a-contract.html)

# Reading Contracts 
Reference link for reading contract practice is [here](https://sunnya97.gitbooks.io/a-beginner-s-guide-to-ethereum-and-dapp-developme/content/basic-practice-reading-contracts.html) 

Try this on the [remix](https://remix.ethereum.org/) and run it on it to check how each function and transaction takes place. Try it with the `Greeter.sol` or `SimpleStorage.sol`.

# Smart Contract ABI
When a smart contract is deployed, it creates a ByteCode and the ABI(Application Binary Interface). The bytecode is unreadable to human and the web application however the ABI translates the bytecode into the json format and this helps with the migrations and all the transactions within the contract and forms a connection with the web3 application interface and the ethereum network. The ABI also regulates the continuous encoding and decoding of all the transactions that are taking place. 

Reference link is [here](https://solidity.readthedocs.io/en/latest/abi-spec.html)

# Declaring Events
```
pragma solidity >= 0.5.0 < 0.6.0;

contract ExampleContract { 

  event LogReturnValue(address indexed _from, int256 _value);

  function foo(int256 _value) public returns (int256) {
     emit LogReturnValue(msg.sender, _value);
     return _value;
  }

}
```
This is how you declare an event called LogReturnValue. Use the event keyword followed by the event name.

A recent update to the Solidity compiler requires the emit keyword before an event is logged. This helps further clarify when events are being logged in the contract code.

Declaring events require that you specify the parameter type as well as a name for the parameter. This parameter name is the name that will appear in the log, so make it descriptive and clear.

You can add the indexed keyword to event parameters. Up to three parameters can receive the indexed attribute. This increases the searchability of events. It is possible to filter for specific values of indexed arguments in the user interface.

Here is a link to the solidity documentation on events.

## Use Cases
The common uses for events can be broken down into three main use cases:

- Events can provide smart contract return values for the User Interface
- They can act as asynchronous triggers with data and
- They can act a cheaper form of storage.
- Get values when transaction is mined
When a transaction is sent via web3.js, a transaction hash is returned, even if the contract functions specifies a return value. Transactions don’t return the contract value because transactions are not immediately mined and included in the blockchain - it takes time (they are asynchronous). You can use an event in the contract function in conjunction with an event watcher in the UI to observe a variable value when the transaction is mined.

## Trigger application logic
You can use an event watcher as a trigger for application logic beyond just reading return values. You could take another action, display a message or update the UI when an event is observed.

## Events as Data Storage
Logs, which are essentially the same as events (the context dictates which term is more appropriate) can also be used as a cheaper form of storage. Logs cost 8 gas per byte whereas contract storage costs 20,000 per 32 bytes, or 625 gas per byte. Logs are cheaper, but also cannot be accessed from any contracts so their use case as storage objects is much more limited. Even still, logs can be useful for aggregating historical reference data.

Events are inheritable members of contracts. You can call events of parent contracts from within child contracts.

When called from within a contract, events cause arguments to be stored in the transaction log, a special data structure in the blockchain. The logs are associated with the address of the contract and will be incorporated into the blockchain, persisting as long as a block is accessible.

Log and event data are not accessible from within contracts, not even from the contract that created the log. Events are useful when interacting with an application. They can provide notifications and confirmations of transactions happening in the smart contract. They are also useful for debugging purposes during development.

Logs are not part of the blockchain per se since they are not required for consensus (they are just historical data), but they are verified by the blockchain as the transaction receipt hashes are stored inside the blocks.

> Remember that events are not emitted until the transaction has been successfully mined.

## When to log events
Logging an event for every state change of the contract is a good heuristic for when you should use events. This allows you to track any and all updates to the state of the contract by setting up event watchers in your javascript files.





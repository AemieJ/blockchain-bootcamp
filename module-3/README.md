# Ethereum Basics - Accounts 
The state is made up of obj called accounts, which each account having a 20 byte address. There are 2 type of contact: 
1. Externally Owned Accounts: only have an associated acc balance of the native system (ethereum). Can transfer a value to another acc or initiate a contract code. 
2. Contract Accounts: Have an ether balance as well as storage state. 

Each acc has nonce.

## Generating accounts 
1. Externally owned acc: When a user generates a private-public keypair, it generates a corresponding acc address too. 
2. Contract acc: can be created by externally owned acc or another contract acc. 

Reference link to this is [here](https://solidity.readthedocs.io/en/v0.4.20/introduction-to-smart-contracts.html#accounts)

# Transactions 
A msg sent from one acc to another by changing the ether balance acc or the storage. In an externally owned acc, it is always signed by the sender with their private key. 

Transactions can optionally include the data as well.

If the receipent of the transaction is a contract acc. When this acc sends a transaction to the contract then it will take the data as an i/p and work on it accordinally. If the target isn't mentioned, it takes in the address of account 0 and creation of contract from this data takes place.

Contains: 
- Recipient address
- Nonce 
- Cryptographic Variables: V(value in wei), R & S
Makes up the sender's signature
- Gas limit or Start gas: the max number of computational steps the transaction execution is allowed to take
- Gas Price: the fee the sender pays per computational step 

Reference link to this is [here](https://solidity.readthedocs.io/en/v0.4.20/introduction-to-smart-contracts.html#transactions)

# Gas & Fees
Executing operations on ethereum cost a fee. Gas fees are incentive for miners as a rewards so miners collects all the gas. 

Each computation on EVM consumes gas. Gas is paid for with ether. Gas limit & price is specified per transaction. Gas limit is the max gas allowed for transaction. Higher gas prices will process the transaction faster. As there is a gas for each operation then we can calculate that and declare a start gas that is sent with transaction to pay for just processing.

Fees help protect the network. If sending transaction was too cheap or free, it could be spammed with bad code. However, fees protects that as it reduces spam and halts bad code.

Reference link to this is [here](https://media.consensys.net/ethereum-gas-fuel-and-fees-3333e17fe1dc)

# Ethereum Strcuture 
It is permisionless system. 
Blockchain features include: 
- State management 
- Trustlessness
- Trackability
- Irreversible 

## EVM
- Runs on every node
- Handle all transaction processing. 
- It is slow!  

## Ethereum network process 
- Transactions are broadcast to the network
- Miners observe this transactions  & Groups into sets called blocks.
- Calc valid block hash when they find they create the block content for it. 

When a valid block is found the block is broadcasted with: 
- Transaction list
- Uncles list
- Block header: 
    - Prev block hash 
    - State root
    - Transaction root
    - Receipts root
    - Block no
    - gas used 
    - timestamp 
    - nonce

> Uncles are a consequence of ethereum short block time and proff of work. A discovered block not included in the main chain is an uncle. Discovering an uncle block is rewarded. 

Required reading [link](https://medium.com/@preethikasireddy/how-does-ethereum-work-anyway-22d1df506369)

The ethereum yellow paper is a must [read](http://gavwood.com/paper.pdf) not completely necessary but as per your deep interest do read. The link above however provides an easier understanding to it.


> None for EOA(externally owned accounts) tracks the number of transactions sent from an account.

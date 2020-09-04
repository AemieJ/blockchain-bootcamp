# Cyrptographic Hash Functions

Hash func is used to map input data of any size to a fixed size and this process is called hashing. Hashing of any input type (song, video, image) will produce a fixed size o/p. 

Properties: 
1. Deterministic
2. Fast
3. Infeasible to reverse (one way func) 
4. Small change in i/p alters the whole o/p 
5. Collision resistant

Used for: 
1. Data integrity ( proves that data is not tampered with) 
2. PoW (hard to find a given hash for a threshold but easier to verify) 
3. Data identification based on the hash

Reference link to this is [here](https://observablehq.com/@consensys-academy/cryptographic-hash-functions)

# Public Key Cryptography
Is a system that use pairs of key. The key pair have unique mathematical property. 
In ethereum, there are derived private keys from master private key and for each derived private key, a public key is generated. THis is done with **elliptical curve cryptography**.

The public key can be shared by anyone. The features: 
1. Encryption: Only the private key holder can decrypt the message encrypted with the corresponding public key.
2. Authentication: Digital Signatures (used for transactions in blockchain)

Reference Link to it is [here](https://ethereum.stackexchange.com/questions/3542/how-are-ethereum-addresses-generated)

# Merkle Trees
Are binary tree data structure. The leaves are hashes of the data. Nodes are hashes of its children.

Features: 
1. Cryptographically authenticated
    - Change of a single data brings in the change for the root
    - The change in the root or the hash of the root can be used to verify the contents. It proves that the data is present within the set.
2. Scalable
3. Doesn't reveal contents of the data. 

## To proof whether a transaction data exists in a merkle tree
From the above merkle tree, if we need to verify that transaction 4 exists, we need to just check the hash of the transaction elements, its sibling and the siblings of their parent nodes. 

## Patricia Trees
They are space optimized version. Allow storage of key-value pairs. It is easily searchable. In ethereum, particia trees are used to store the account balance of every acc. 

### Reference links 
[Merkle Trees](https://observablehq.com/@consensys-academy/merkle-trees)  
[Ever Wonder How Merkle Trees Work? by ConsenSys Media](https://media.consensys.net/ever-wonder-how-merkle-trees-work-c2f8b7100ed3)  
[Patricia Merkle Trees](https://eth.wiki/en/fundamentals/patricia-tree)

# Blockchain Structure
Here, it is the system in which each participants agree to a state using the digital signatures.

Updates are broken into sets (blocks) 
- summarized with a merkle root
- root hash included in a block of data along with the updates so all transactions are valid.

A simple block includes 
- a list of transactions 
  - a merkle tree based on the list 
- hash of the prev block so the chain is maintained 
- nonce: modified by miners 
  - used in PoW
  - the modification is to find a block hash less than the target difficulty

**Created blocks are immutable.** 

Reference link to this is [here](https://andersbrownworth.com/blockchain/)  
Blockchain notebook is [here](https://observablehq.com/@consensys-academy/building-a-blockchain)
Good video on [difficulty](https://www.youtube.com/watch?v=o1gOyhU6XEw)

# Smart Contracts 
Digitally execute terms of a contract
- Trustless - No 3rd party, univerally accessible 
- Trackable 
- Irreversible 
- Self-executing

Buterin defines Smart Contracts as “cryptographic 'boxes' that contain value that only unlock if certain conditions are met”.

Meaning that through the use of Smart Contracts, developers can define their own instructions to the Ethereum Virtual Machine, or EVM, allowing digitally binding agreements to be coded on a public ledger. This enables anyone to build a wide array of decentralized applications that have the capability to potentially disrupt numerous industries.

Today, with the tremendous growth of the Ethereum community, developers have several options when deciding on which Turing-complete programming language they would like to use to build their Smart Contracts and decentralized application logic, the most notable being Solidity.

## Programming languages for ethereum 
- Solidity 
- Vyper
- LLL (Low-level lisp like language) - deprecated

Reference link is [here](https://solidity.readthedocs.io/en/develop/introduction-to-smart-contracts.html#)

# Nodes 
Genrally the structure is server based which is naturally slow and a huge BW demand on the server. Thus, peer-to-peer network is preferred as no priviliged users. Blockchain run on peer-to-peer net. 

Node participate by running the right software. A computer could be either used as bitcoin or ethereum node based on the setup of the software.

Nodes act as a gateway in the participation.

Node can participate in 3 ways: 
- Run a light client (shallow copy of the blockchain, nodes only verify small part of blockchain) 
- Full node (full copy of the blockchain)
- Mining (a full node + verify transactions). 

Fast Sync vs full sync link is [here](https://www.youtube.com/watch?v=4GMIdPt_uTw&feature=youtu.be&t=243)

# Blockchain forks 
A fork occurs when blockchain splits into 2 concurrent into 2 blockchains. 
- Intentional or unintentional 
- Network changes
- Community disagreement
- Hard fork if there is not an agreement on the state of the blockchain 
- Soft fork

## Hard fork 
The new chain is incompatible with the old one. The 2 chains can never meet again. Generally, used if a clear consensus is established around achanged. 

## Soft fork 
Backward compatible with the old chain. New block rules are stricter and follow that of the old chain as well. 

## Unintentional forks
Occurs when 2 miners work on particular block and broadcast on the network. When one chain is gets the longer chain then that becomes the primary chain to follow. 

Reference link is [here](https://www.coindesk.com/short-guide-bitcoin-forks-explained)
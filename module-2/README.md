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
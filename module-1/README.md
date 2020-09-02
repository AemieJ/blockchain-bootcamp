# Distributed Ledgers

## Ledgers 
The formation of accounting and transaction taking place. Generally, it is under a centralized structure where a central administrator has the highest authority. 
In ledgers, transactions takes place which needs to be durable, consistent and atomic. 

## Distributed Ledgers 
Comes with the fact of the decentralized structure where the transactions is made public among the users itself and removed the centralized admin. The transaction takes place with the 
encryption and decryption of crypted signatured. However, this takes time as the users involved in the ledger needs to come in consensus. 

# Consensus Mechanisms 
This mechanism facilitates the agreement between the participants to guarantee data consistency. Each participant must have the same ledger itself.
The problems that is addressed by consensus is done by the **Byzantine General Problem** where the general needs to come to a consensus to either attack or retreat. However, messages can be lost or mistranslated. The fault tolerance helps in resolving where the majority comes to the consensus for the state of the system. 

- Proof Of Work (used by Bitcoin & Ethereum )
The miner checks which blocks are valid by checking when the block hash is less than the target difficulty. The difficulty is increased after every nonce. This is highly expensive. 
- Proof of Stake (a better approach )
Is the consensus mech where the currency holders stake some currency for the chance to determine the valid block. The holder is then selected depending upon their stake. There are different types including leased ( reward among the holders ), delegated ( only 1 selected and gets rewarded). Can be used for high transaction volumes.
- PBFT ( high performance )

Reference link to this is [here](https://mastanbtc.github.io/blockchainnotes/consensustypes/).

# Mining 
This is majorly a guessing game where it is difficult to guess it but verifying it is simple. The difficulty is raised depending on how fast the guess is achieved in the game. This valid guess creates a valid block which included transactions, block hash, prev block hash, and also the nonce. The one who mines this get the miner reward. 

If block A guessed before block D and has been validated by block B and C, then only block A will receive the reward. 

# Public & Private Blockchains 

## Public Blockchains 
The participants are available publicily. The read and write of data could be done by any participant. Transactions to prevent fraud is done through PoW, and PoS

### Consortium Blockchains
Public blockchains where only verified participants are allowed. Can achieve higher transaction throughput.

## Private Blockchain
Prototyping and deployment solutions are the major user cases. You're aware of the participants involved in this. 

Reference link to this is [here](https://blog.ethereum.org/2015/08/07/on-public-and-private-blockchains/).



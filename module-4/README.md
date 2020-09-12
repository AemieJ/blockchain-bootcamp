# Decentralized App Development

## When to use blockchain? 

- Is the system defining digital relationships? Yes.
- Should data be dynamic & auditable? Yes.
- Should data be managed by central authority? No.
- Is the speed of the network imp? No.

If for the following listed ques, the answers are as provided, then a blockchain is a good solution to the problem you're solving. 

## Core developer tools & components 
- Blockchain: Ethereum protocol
- Infrastructure: Infura
- Dev tools: Truffle
- Core Components: Metamask, Uport

Here you see important differences between a Web 2.0 Application (client-server) and a Web 3.0 Decentralized Application (front-end + blockchain):

1. The computing of web2 apps happens in servers while for web3 dapps happens in a p2p network
2. Web2 apps are hosted in web servers while web3 dapps can be hosted in distributed networks
3. The service layer of web2 apps is made of HTTP APIs (e.g. REST) while in web3 it's built on p2p protocols
4. In web2, information is stored in databases, while in web3 it is stored in the blockchain and other decentralized networks

# Development environment setup options
## Ethereum networks 
- Ethereum mainnet
- Testnets
- Private network

Make use of each for difference phase of the development of application.  
Private network > Public test network (ropsten, rinkeby) > ethereum mainnet

## Connecting to a blockchain 
- Geth -> to connect public/private blockchains
- Ganache -> local private development blockchain 
- Remix -> blockchain simulator (local, private) 
- Metamask -> public/private blockchains

## Development workflow 
Create acc -> Fund acc -> develop -> compile -> sign & develop -> interact & test  
1. For creating acc 
    - Geth : good during debugging and testing
    - Metamask 
    - Ganache 
    - Remix
    
2. Funding acc 
    - Private blockchain: Ganahce/Remix
    - Test nets: faucets

3. Compile 
    - Remix
    - SolC
    - Truffle

4. Sign & Deploy
    - Mist
    - Remix
    - Truffle: best tools for sophisticated contracts

5. Interact & Test 
    - Remix
    - Metamask 
    - Truffle

# Key Developer Tools 
## Geth
Geth is a gateway to the ethereum network, also known as node.
- Connect to a blockchain or create one 
- Create & manage acc 
- Fund with mining or transfers on test net
- Deploy compiled contract 

## Parity 
Parity is an ethereum client very similar to geth but with bit more functionality 
- Client similar to geth 
- Comes with multi-signature wallet 
- Comes with web3 enabled software
- Is highly popular 
 
# Installing geth & using geth to connect to private blockchain 

    $ geth --datadir . init genesis.json
The last line of output in the console should say Successfully wrote genesis state. Now we can start the private network so we can mine blocks on the private chain.

In case of Fedora, run the following command after you've created accounts using geth:  

    $ geth --nodiscover --networkid 42 --datadir .ethereum/ --unlock <ethereum address> --mine --rpc --rpcapi eth,net,web3 --rpcaddr localhost --allow-insecure-unlock

# Connecting to Testnets and Exploring the Blockchain with Geth
Geth is your portal to any Ethereum network. It can take a long time and a lot of storage to sync a full geth node, so there are several sync options that geth comes with.

A "full" sync gets the block headers, the block bodies, and validates every element from genesis block. This runs a full node on your machine, which keeps the entire current state of the blockchain and validates incoming blocks. This is not to be confused with an archive node, which does this but also stores the entire transaction history of the blockchain.

A "fast" sync gets the block headers, the block bodies, it processes no transactions until current block - 64. Then it gets a snapshot state and goes like a full synchronization. During a fast sync, you can get all of the blocks while still not be completely in sync because the account state may still not be available (ie. balances, nonces, smart contract code and data). These need to be downloaded separately and cross checked with the latest blocks. This phase is called the state trie download and it actually runs concurrently with the block downloads and it can take a lot longer nowadays than downloading the blocks.

A "light" sync gets only the current state. To verify elements, it needs to ask to full (archive) nodes for the corresponding tree leaves.

In this exercise, we will use "light" sync because it is the fastest.

Connect to a testnet
Connecting to testnet with geth is very simple. To connect to the Rinkeby testnet, simply run the following in the command line. We will also add options to launch the console so we can interact with the testnet from the terminal.

$ geth --rinkeby --syncmode fast console
Wait for the terminal to say that the blockchain is syncing

INFO [09-11|14:14:28.922] Block synchronisation started
Once block synchronization has started, you can start investigating the blockchain up to the point at which your node is synced.

Check the status of your node with eth.syncing. You should see something like this

> eth.syncing
{
  currentBlock: 1846452,
  highestBlock: 2970863,
  knownStates: 0,
  pulledStates: 0,
  startingBlock: 1841089
}
This data will be updated as your node syncs with the network.

Retrieving Block data
You can then get the information about a given block, say block 1830000.

> eth.getBlock(1830000)
{
  difficulty: 2,
  extraData: "0xd783010802846765746887676f312e392e34856c696e7578000000000000000042eb768f2244c8811c63729a21a3569731535f066635f83421bf059cd8111f180f0727128685bae47ffc57839b00206d1ad20c69a1981b489f772031b279182d99e65703f0076e4812653aab85fca0f0d6ae8250b8348c94847280928c79fb3b63ca453efc18cbc391de84dbd87db83b20935d3e89f5dd91b239241f4286de636a1c1d431d162611438e5fe8a148b6ff13c4422ff4212ac94a35b271da789fa309f485e7be631f5322cc9ac22eedc9986414dd089afd92f800",
  gasLimit: 7212968,
  gasUsed: 741031,
  hash: "0xa20b9701c16c2c17cf5a844dba59b33530913bb227bbf17cf5ecb052d2b287b7",
  logsBloom: "0x00000000000000000000008000000000000000000000200080000000000000000000000000000000000000000000000000000000000000000000008200000000000000000000000000000008000000000000000000000400000000000000000800001000000000400000008000000000000000100000040000000010000000000400000000000000000000000000000000010000020000000000000000000200000000000000400000000000000000000001000000000000000000400000000000000002000000000001000000000000000020000000000000000000000000000000000000000400000000001000000400000000000000000000000020020100",
  miner: "0x0000000000000000000000000000000000000000",
  mixHash: "0x0000000000000000000000000000000000000000000000000000000000000000",
  nonce: "0x0000000000000000",
  number: 1830000,
  parentHash: "0x61aceb1112c79f12fd4acae7d5c263f58c0cfc23cabf996d0f81d3426c9db5fc",
  receiptsRoot: "0x18cd5444fbc45c3b45536ee1c0d66ff1498a43425ca8f4e7594af25bd87ad2fe",
  sha3Uncles: "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
  size: 2092,
  stateRoot: "0x84c27ff36faabd161a5c850906581df27fa758bccdf9ac660602399ecca39972",
  timestamp: 1519519986,
  totalDifficulty: 3388435,
  transactions: ["0x77dd615bcc63322f436a747f43d02f7ad15ebbf7867c7dbb065e6a1a4d58a2cf", "0xa367a991aaa44b602247d5d12e748dc216fc71a8cd1408107076643094d83377", "0xf6dc6e3cbca47eaee35f7368372e2fb4336d4c7869ba4447d785c2af63545caf", "0xab50463b9617b6fdea0b4c6f8c80607608c36918a33c3b45dfd2d336ced7d50a"],
  transactionsRoot: "0x130985bb247d15b853dca099ad8d9f900a1d24ea2a68828b63530ef7090b7dad",
  uncles: []
}
Notice that the miner address is "0x0000...0000" and the nonce is also zeros. This is because the Rinkeby network does not run on proof of work. Rinkeby is a proof-of-authority test network running the Clique consensus protocol. A proof-of-authority network relies on trusted nodes designated as “signers” that have the ability to create blocks. A majority of signers on the network are required to validate the chain. Rinkeby has seven designated signers maintained by the following groups:

Ethereum Foundation (3)
Infura (1)
Oraclize (1)
Augur (1)
Akasha (1)
Retrieving Transaction data
You can get the information about any transactions from your local node as well, say transaction at index 0 of block 1830000.

> eth.getTransaction(eth.getBlock(1830000).transactions[0])
{
  blockHash: "0xa20b9701c16c2c17cf5a844dba59b33530913bb227bbf17cf5ecb052d2b287b7",
  blockNumber: 1830000,
  from: "0xb840f68af2624c761adc42a365d99dd470f73d08",
  gas: 47197,
  gasPrice: 15000000000,
  hash: "0x77dd615bcc63322f436a747f43d02f7ad15ebbf7867c7dbb065e6a1a4d58a2cf",
  input: "0xde5f72fd",
  nonce: 11,
  r: "0x53b2e2bd0f77701d697d7d7579f86ff433bfc87cf50b1f0f53da62f2b0b2f9d8",
  s: "0x2adc0b0a3dbd8719eb1d994a4fac0fa11fb3d74b8c51a480142056a202dac7c6",
  to: "0x832b52302b89fa8e703cc12db1b6049984d6fef7",
  transactionIndex: 0,
  v: "0x2c",
  value: 0
}
Retrieving Contract data
You can also retrieve the code of any deployed contract, so long as you have the address. Try

eth.getCode("0x832b52302b89fa8E703Cc12dB1B6049984d6fEF7")
It should print out a giant string of hexadecimal. This is the deployed contract's code. To check the storage of a contract you can use the eth.getStorageAt() method.

eth.getStorageAt("0x832b52302b89fa8E703Cc12dB1B6049984d6fEF7")
"0x000000000000000000000000000000000000000000004a1d89bb94865ec00000"
The output is the storage of the contract. The layout of the contract depends on how the smart contract is written. You can learn more about the details here.

Note that this storage value changes as users interact with and update contract storage. The current value reflects the state of the contract at the highest block that you are currently synced with, so if you are not fully synced with the blockchain you are looking at a historical state of the blockchain. This is also true with account balances. Checking your account balance on a node that is not fully synced with the network will reflect a historical account balance.

Get some test ether
Stop syncing your fast sync node. Let's sync a light node, which is way smaller and faster. There is less blockchain data available when you a running a light node, but you can still query some data and send transactions to the network.

$ geth --rinkeby --syncmode light console
Remember you can silence the terminal logs with debug.verbosity(0).

While the light node is syncing (it should take on the order of minutes) get some test ether here.

You will need to create a new account on your rinkeby geth node, if there is not one already. You can check your accounts with eth.accounts and create a new one with personal.newAccount().

Copy your address, post in on social media and then input the link to the post in the input field. Your request should fund the account in less than a minute. Now check your balance, you should have some testnet ether!

> eth.getBalance(eth.accounts[0])
3000000000000000000 // in wei (equal to 3 ether)
You can use this test ether to pay gas fees for sending transactions and deploying contracts on the testnet.

If you run into an error

Error: no suitable peers available at 
        web3.js:3143:20 
        at web3.js:6347:15 
        at web3.js:5081:36 
        at anonymous:1:1


try adding a peer to your node with this command

admin.addPeer("enode://05b03241bae2a17534a4ffa005d075e38868f89c6db95b0e089c67ff6d3e9ed3f7132d4e9d57f09628f4827cfb370fe5f624c36af44899e423aacf4869a3adf3@13.124.4.106:30303"); per this post.

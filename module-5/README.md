# Development workflow: A low-level overview

`geth --dev console` and check whether your ether acc has any ether.

```
simpleStorage.sol
pragma solidity ^0.4.0;

contract SimpleStorage {
    uint storedData;

    function set(uint x) public {
        storedData = x;
    }

    function get() public constant returns (uint) {
        return storedData;
    }
}
```

# The Ganache CLI

Installing and making use of `ganache-cli`:
```
$ npm install -g ganache-cli
$ ganache-cli
```

# The truffle CLI 
Installing and make use of `truffle`: 
```
$ npm install -g truffle
$ truffle init
```

# The structure of a truffle project 
Contract is created using the binary and abis.
1. `truffle init`: creates the entire truffle project structure
2. `truffle-config.js` and `truffle.js` performs same config operations. Windows users make use of the config file while the linux and mac osx users make use of the individual file provided only.

Use boxes to create the built-in template structures.
To unbox the truffle boxes, for instance metacoin, it will be done as followed: 

```
$ mkdir metacoin && cd metacoin
$ truffle unbox metacoin 
$ truffle compile 
$ truffle migrate 
$ truffle test 
```
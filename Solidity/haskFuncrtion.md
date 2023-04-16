---
layout: home
title: Hash functions
parent: Solidity
---

# Hash Function
A cryptographic hash Function (CHF) is a mathematical algorithm that maps data of arbitrary size
(aften called the "message") to a bit array of a fixed size (the "hash value", "hash", or "message digest").<br>
It is a one-way function, that is, a function which is practically infeasible to invert or reverse the computation.

Solidity provides inbuilt cryptographic functions as well. Following are important methods:
1. keccak256(bytes memory) returns (bytes32) — computes the Keccak-256 hash of the input.
2. sha256(bytes memory) returns (bytes32) — computes the SHA-256 hash of the input.
3. ripemd160(bytes memory) returns (bytes20) — compute RIPEMD-160 hash of the input.


Keccak is a leading hashing function, designed by non-NSA designers. Keccak won NIST conpetition to become the official SHA3
Keccak is a family of cryptographic sponge functions and is designed as an alternative to SHA-256

## keccak256 
Example:- 1
```c++
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.7.0 <0.9.0;
 
contract GenerateRandomNumber {
    function randMod(uint256 range) external view returns (uint256) {
        //abi.encodePacked concatonates arguments
        return
            uint256(
                keccak256(
                    abi.encodePacked(
                        block.timestamp,
                        block.difficulty,
                        msg.sender
                    )
                )
            ) % range;
    }
}
```

Example:-2
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.7.0 <0.9.0;
 
contract ContractOracle {
    address admin;
    uint256 rand;
 
    constructor(address sender) {
        admin = sender;
    }
 
    modifier onlyOwner() {
        require(admin == msg.sender, "msg sender not authorized!");
        _;
    }
 
    function setrand(uint256 _in) public onlyOwner {
        rand = _in;
    }
 
    function getRand() public view returns (uint256) {
        return rand;
    }
}
    contract GenerateRandomNumber {
    ContractOracle oracle;
 
    constructor() {
        oracle = new ContractOracle(msg.sender);
    }
 
 
    function hashFunction(uint256 _range) public view returns (uint256) {
        return
            uint256(
                keccak256(
                    abi.encodePacked(
                        block.difficulty,
                        block.timestamp,
                        msg.sender,
                        oracle.getRand()
                    )
                )
            ) % _range;
    }
}
```
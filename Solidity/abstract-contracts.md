---
title: Abstract contracts
layout: home
parent: Solidity
---

## Abstract Contract
Abstract Contract is one which contains at least one function without any implementation. Such a contract is used as a base contract. Generally an abstract contract contains both implemented as well as abstract functions. Derived contract will implement the abstract function and use the existing functions as and when required.

In case, a derived contract is not implementing the abstract function then this derived contract will be marked as abstract.

Example: 1
```c++
pragma solidity ^0.5.0;

contract Calculator {
   function getResult() public view returns(uint);
}
contract Test is Calculator {
   function getResult() public view returns(uint) {
      uint a = 1;
      uint b = 2;
      uint result = a + b;
      return result;
   }
}
```

<hr>

Example: 2
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.8.6 <0.9.0;
 
// Base
abstract contract X {
    // mark abstruct keyword here
    function y() public pure virtual returns (string memory); // mark virtual keyword here
}

// Derived
contract Z is X {
    function y() public pure override returns (string memory) {
        // mark override keyword here and function name is same in both function and abstract
        return "hello";
    }
}
```

<hr>

Example: 3
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.8.6 <0.9.0;
 
// technically contract is still abstract since it has at least one function without a body
contract Member {
    string name;
    uint256 age = 38;
 
    // because function setNme has no body the contract is now abstract
    function setName() public virtual returns (string memory) {}
 
    function returnAge() public view returns (uint256) {
        return age;
    }
}
 
// derived contract
contract Teacher is Member {
    function setName() public pure override returns (string memory) {
        return "tom";
    }
}
```
---
layout: home
title: Inheritance
parent: Solidity
---

## Inheritance
Inheritance is a way to extend functionality of a contract. Solidity supports both single as well as multiple inheritance. Following are the key highlighsts.

* A derived contract can access all non-private members including internal methods and state variables. But using this is not allowed.

* Function overriding is allowed provided function signature remains same. In case of difference of output parameters, compilation will fail.

* We can call a super contract's function using super keyword or using super contract name.

* In case of multiple inheritance, function call using super gives preference to most derived contract.

Example
```c++
pragma solidity ^0.5.0;

contract C {
   //private state variable
   uint private data;
   
   //public state variable
   uint public info;

   //constructor
   constructor() public {
      info = 10;
   }
   //private function
   function increment(uint a) private pure returns(uint) { return a + 1; }
   
   //public function
   function updateData(uint a) public { data = a; }
   function getData() public view returns(uint) { return data; }
   function compute(uint a, uint b) internal pure returns (uint) { return a + b; }
}
//Derived Contract
contract E is C { // direct inheritenct
   uint private result;
   C private c; // inheritence using new keyword
   constructor() public {
      c = new C();
   }  
   function getComputedResult() public {      
      result = compute(3, 5); // internal function available via direct inheritace using 'is' keyword
   }
   function getResult() public view returns(uint) { return result; }
   function getData() public view returns(uint) { return c.info(); }
}
```

Example 2 
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

contract C {
    uint256 private data;
    uint256 public info;

    constructor() {
        info = 10;
    }

    function increment(uint256 a) internal pure returns (uint256) {
        return a + 1;
    }

    function duplicateData(uint256 a) public {
        data = a;
    }

    function getData() public view returns (uint256) {
        return data;
    }

    function campute(uint256 a, uint256 b) internal pure returns (uint256) {
        return a + b;
    }
}

contract D { 
    C c = new C(); // only public state variable and functions are available using this method

    function readInfo() public view returns (uint256) {
        return c.info();
    }
}
```
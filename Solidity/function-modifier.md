---
title: Function modifiers
parent: Solidity
layout: home
---
## Function modifiers
Function Modifiers are used to modify the behaviour of a function. For example to add a prerequisite to a function.

First we create a modifier with or without parameter.
```c++
contract Owner {
   modifier onlyOwner {
      require(msg.sender == owner);
      _;
   }
   modifier costs(uint price) {
      if (msg.value >= price) {
         _;
      }
   }
}
```
The function body is inserted where the special symbol "_;" appears in the definition of a modifier. So if condition of modifier is satisfied while calling this function, the function is executed and otherwise, an exception is thrown.

See the example below −
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

contract Owner {
   address owner;
   constructor() public {
      owner = msg.sender;
   }

   modifier onlyOwner() {
       // customizable logic to modify our function
       require(msg.sender == owner, "message sender not equal to owner");
       _; //mark the underscore followed by semi-colon. This means continue only if requirement is met.
   }

   modifier costs(uint price) {
      if (msg.value >= price) {
         _;
      }
   }
}
contract Register is Owner {
   mapping (address => bool) registeredAddresses;
   uint price;
   constructor(uint initialPrice) public { price = initialPrice; }
   
   function register() public payable costs(price) {
      registeredAddresses[msg.sender] = true;
   }
 
   // onlyOwner is our function modifier that requires
   // only the owner to be able to change the price
   function changePrice(uint256 _price) public onlyOwner {
       price = _price;
   }
}
```
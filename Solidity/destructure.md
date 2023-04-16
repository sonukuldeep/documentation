---
layout: home
title: Destructure
parent: Solidity
---

Example:-1
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.7.0 <0.9.0;
 
contract MultiReturn {
    function ret() public pure returns (uint256 res, uint256 res2) {
        res = 1 + 2;
        res2 = res + 2;
    }
}
 
contract Destructure {
    string public tom = "Hello!";
    uint256 public changeValue;
 
    function destructureFunction()
        public
        view
        returns (
            uint256,
            bool,
            string memory
        )
    {
        return (1 + 2, true, tom); // notice the parentheses here
    }
 
    function changeVal() public {
        (changeValue, , ) = destructureFunction(); // the 2nd and 3rd value will pass since no variable is present to accept value
    }
}
```
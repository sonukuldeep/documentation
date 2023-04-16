---
title: Scope
parent: Solidity
layout: home
---

Scope in solidity

    private: can only be accessed from inside.

    public: : can be accessed from inside and outside

    external: can only be accessed from outside

    internal: can be accessed from inside and outside provided it is inherited using 'is' keyword.

Example: 
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

contract C {
    uint256 private data; // available only inside
    uint256 public info; // available inside and outside

    constructor() {
        info = 10;
    }

    function duplicateData(uint256 a) public {
        data = a;
    }

    function getData() public view returns (uint256) {
        return data;
    }

    function campute(uint256 a, uint256 b) internal pure returns (uint256) { // available inside and ouside only if inherited using 'in' keyword
         return a + b;
    }
}

contract E is C { // inherited directly
    uint256 internal result;
    C c; // inherited using new instance

    constructor() {
        c = new C();
    }

    function getComputedResult() public pure {
        campute(23, 5); // note c.campute is not available since the campute function is 'internal'
                        // but since I inherited 'C' using 'is' operator we can access it directly
    }

    function getResult() public pure returns (uint256) {
        return 1;
    }

    function getInfo() public view returns (uint256) {
        return c.info();
    }
}
```
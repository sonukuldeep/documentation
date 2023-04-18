---
layout: home
parent: Solidity
title: Libraries
---

## Libraries
Libraries are similar to Contracts but are mainly intended for reuse. A Library contains functions which other contracts can call. Solidity have certain restrictions on use of a Library. Following are the key characteristics of a Solidity Library.

* Library functions can be called directly if they do not modify the state. That means pure or view functions only can be called from outside the library.

* Library can not be destroyed as it is assumed to be stateless.

* A Library cannot have state variables.

* A Library cannot inherit any element.

* A Library cannot be inherited.

Example: -1
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.0 <0.9.0;

library Search {
    //mark self keyword here
    function indexOf(uint256[] storage self, uint256 value)
        public
        view
        returns (uint256)
    {
        for (uint256 i = 0; i < self.length; i++) {
            if (self[i] == value) return i;
        }
        return 0;
    }
}

contract SearchLibrary {
    uint256[] data;

    constructor() {
        for (uint256 i = 1; i < 6; i++) {
            data.push(i);
        }
    }
    
    function isValuePresent(uint256 val) external view returns (uint256) {
        return Search.indexOf(data, val); // mark how library function is called here
    }
}
```

Example:- 2
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.0 <0.9.0;

library Search {
    function indexOf(uint256[] storage self, uint256 val)
        public
        view
        returns (uint256)
    {
        for (uint256 i = 0; i < self.length; i++) {
            if (self[i] == val) return i;
        }
        return 0;
    }
}

contract SearchFrom {
    // using A for B library pattern assignment
    using Search for uint256[];
    uint256[] data;

    constructor() {
        data.push(1);
        data.push(2);
        data.push(3);
        data.push(4);
        data.push(5);
    }

    function getIndex() external view returns (uint256) {
        uint256 val = 4;
        return data.indexOf(val); // insanly smart. essenctially we are creating a custom function for data here!!!
    }
}
```

Example:- 3
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.0 <0.9.0;

library Arithmatic {
    function add(uint256 _a, uint256 _b) external pure returns (uint256) {
        uint256 sum = _a + _b;
        return sum;
    }

    function substract(uint256 _a, uint256 _b) external pure returns (uint256) {
        uint256 sum;
        if (_a > _b) sum = _a - _b;
        else sum = _b - _a;
        return sum;
    }

    function multiply(uint256 _a, uint256 _b) external pure returns (uint256) {
        uint256 sum = _a * _b;
        return sum;
    }

    modifier checkZero(uint256 _b) {
        require(_b > 0, "Denominator cannot be zero");
        _;
    }

    function divide(uint256 _a, uint256 _b)
        external
        pure
        checkZero(_b)
        returns (uint256)
    {
        uint256 sum;
        sum = _a / _b;
        return sum;
    }
}

contract PerformArithmatic {
    function add(uint256 _a, uint256 _b) external pure returns (uint256) {
        return Arithmatic.add(_a, _b);
    }

    function subtract(uint256 _a, uint256 _b) external pure returns (uint256) {
        return Arithmatic.substract(_a, _b);
    }

    function multiply(uint256 _a, uint256 _b) external pure returns (uint256) {
        return Arithmatic.multiply(_a, _b);
    }

    function divide(uint256 _a, uint256 _b) external pure returns (uint256) {
        return Arithmatic.divide(_a, _b);
    }
}
```
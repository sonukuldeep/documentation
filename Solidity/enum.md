---
layout: home
title: Enums
parent: Solidity
---
## Enums
Enums restrict a variable to have one of only a few predefined values. The values in this enumerated list are called enums.

### Example:
```c++
enum FreshJuiceSize { SMALL, MEDIUM, LARGE }
FreshJuiceSize choice;
FreshJuiceSize constant defaultChoice = FreshJuiceSize.MEDIUM;
```
## Example:
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

contract EnumExercise {
    enum frenchFriesSize {
        LARGE,
        MEDIUM,
        SMALL
    }

    frenchFriesSize choice;
    frenchFriesSize constant defaultChoice = frenchFriesSize.MEDIUM;

    function setSmall() public payable {
        choice = frenchFriesSize.SMALL;
    }

    // without setSmall function being called above if you click get choice it will return 0 i.e value set to first index by default which in this case is large!
    // Note this again returns an uint.
    function getChoice() public view returns (frenchFriesSize) {
        return choice;
    }

    function getDefault() public pure returns (uint256) {
        return uint256(defaultChoice);
    }
}
```
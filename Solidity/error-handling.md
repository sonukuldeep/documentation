---
layout: home
parent: Solidity
title: Error handling
---

ERROR HANDLING!!!
Solidity has functions that help with error handling
A way of tackling this is that when an error happens, the state reverts back to its original state.
Below are some of the important methods for error handling:
    1. assert(bool condition) — In case condition is not met, this method call causes an
invalid opcode and any changes done to state get reverted. This method is to be used for internal errors.
    2. require(bool condition) — In case condition is not met, this method call reverts to original state.
This method is to be used for errors in inputs or external components.
    3. require(bool condition, string memory message) — In case condition is not met, this method call reverts to original state.
This method is to be used for errors in inputs or external components. It provides an option to provide a custom message.
    4. revert() This method aborts the execution and revert any changes done to the state.
    5. revert(string memory reason) This method aborts the execution and revert any changes done to the state.
It provides an option to provide a custom message.

```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.0 <0.9.0;

contract LearnErrorHandling {
    bool public sunny = true;
    bool public umbrela = false;
    uint256 public finalCalc = 0;

    // finalCalc can never equal 6
    function internalTestUnits() internal view {
        assert(finalCalc != 6);
    }

    //solar panel machine
    function solarClac() public {
        require(sunny, "Hey its not sunny today");
        finalCalc += 3;
        assert(finalCalc != 6); // Assert will make sure the condition is always met else transaction will revert
    }

    //machine that controls the weather
    function changeWeather() public {
        sunny = !sunny;
    }

    // grab final calc
    function bringUmbrella() public {
        if (!sunny) umbrela = true;
        else revert("No need to bring an umbrella today!!");
    }
}
```
---
layout: home
parent: Solidity
title: Events
---

# Events
Events are an abstraction of the Ethereum logging/event-watching protocol. Log entries provide the contract’s address, a series of up to four topics and some arbitrary length binary data. Events leverage the existing function ABI in order to interpret this (together with an interface spec) as a properly typed structure.

Given an event name and series of event parameters, we split them into two sub-series: those which are indexed and those which are not. Those which are indexed, which may number up to 3 (for non-anonymous events) or 4 (for anonymous ones), are used alongside the Keccak hash of the event signature to form the topics of the log entry. Those which are not indexed form the byte array of the event.
[more](https://docs.soliditylang.org/en/v0.8.19/abi-spec.html#events)

```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.6 <0.9.0;

// 1. declare the event
// 2. then emit the event

contract LearnEvents {
    // index causes higher gas so limit index to 3
    event NewTrade(uint256 indexed date, address from, address indexed to, uint256 indexed amount);

    function trade(address to, uint256 amount) external {
        // outside consumer can see the event through web3js
        // block.timestamp is a global variable that gives the current timestamp
        emit NewTrade(block.timestamp, msg.sender, to, amount);
    }
}
```
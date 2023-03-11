---
layout: home
title: Mapping
parent: Solidity
---
## Mapping 
Mapping is a reference type as arrays and structs. <br>
Following is the syntax to declare a mapping type.
```c++
mapping(_KeyType => _ValueType)
```
Where

    _KeyType − can be any built-in types plus bytes and string. No reference type or complex objects are allowed.

    _ValueType − can be any type.

### Considerations

* Mapping can only have type of storage and are generally used for state variables.

* Mapping can be marked public. Solidity automatically create getter for it.

Example:
```c++
pragma solidity ^0.5.0;

contract LedgerBalance {
   mapping(address => uint) public balances;

   function updateBalance(uint newBalance) public {
      balances[msg.sender] = newBalance;
   }
}
contract Updater {
   function updateBalance() public returns (uint) {
      LedgerBalance ledgerBalance = new LedgerBalance();
      ledgerBalance.updateBalance(10);
      return ledgerBalance.balances(address(this));
   }
}
```

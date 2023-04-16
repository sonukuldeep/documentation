---
layout: home
title: Fallback functions
parent: Solidity
---

## Fallback Functions
Fallback function is a special function available to a contract. It has following features −

    It is called when a non-existent function is called on the contract.

    It is required to be marked external.

    It has no name.(anonymous)

    It has no arguments

    It can not return any value.

    It can be defined one per contract.

    If not marked payable, it will throw exception if contract receives plain ether without data.

Following examples show the concept of a fallback function per contract.

Example:-1
```c++
contract Fallback {
    event Log(uint256 gas);
 
    fallback() external payable {
        // not recomended to write much code in here - because the function will fail if it uses too much gas
        // invoke send method: we get 2300 gas which is enough to emit a Log
        // invoke call method: we get all the gas
        // special solidity function gasZeft returns how much gas is left
        emit Log(gasleft());
    }
 
    function getBalance() public view returns (uint256) {
        return address(this).balance; // this refers to caller here
    }
}
 
contract SentToFallback {
    function transferToFallback(address payable _to) public payable {
        _to.transfer(msg.value);
    }
 
    function callFallback(address payable _to) public payable {
        (bool sent, ) = _to.call{value: msg.value}("");
        require(sent, "Failed to send");
    }
}
```

Example:-2
```c++
pragma solidity ^0.5.0;

contract Test {
   uint public x ;
   function() external { x = 1; }    
}
contract Sink {
   function() external payable { }
}
contract Caller {
   function callTest(Test test) public returns (bool) {
      (bool success,) = address(test).call(abi.encodeWithSignature("nonExistingFunction()"));
      require(success);
      // test.x is now 1

      address payable testPayable = address(uint160(address(test)));

      // Sending ether to Test contract,
      // the transfer will fail, i.e. this returns false here.
      return (testPayable.send(2 ether));
   }
   function callSink(Sink sink) public returns (bool) {
      address payable sinkPayable = address(sink);
      return (sinkPayable.send(2 ether));
   }
}
```
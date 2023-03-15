---
title: Function overload
layout: home
parent: Solidity
---

## Function overload
You can have multiple definitions for the same function name in the same scope. The definition of the function must differ from each other by the types and/or the number of arguments in the argument list. You cannot overload function declarations that differ only by return type.

Following example shows the concept of a function overloading in Solidity.
Example
```c++
pragma solidity ^0.5.0;

contract Test {
   function getSum(uint a, uint b) public pure returns(uint){      
      return a + b;
   }
   function getSum(uint a, uint b, uint c) public pure returns(uint){      
      return a + b + c;
   }
   function callSumWithTwoArguments() public pure returns(uint){
      return getSum(1,2);
   }
   function callSumWithThreeArguments() public pure returns(uint){
      return getSum(1,2,3);
   }
}
```
Run the above program using steps provided in Solidity First Application chapter.

Click callSumWithTwoArguments button first and then callSumWithThreeArguments button to see the result.
---
layout: home
title: Functions
parent: Solidity
---

## Function
Function in Solidity is defined using the function keyword, followed by a unique function name, a list of parameters (that might be empty), and a statement block surrounded by curly braces.

### Syntax
```c++
function function-name(parameter-list) scope returns() {
   //statements
}
```
### Example:
```c++
pragma solidity ^0.5.0;

contract Test {
   function getResult() public view returns(uint){
      uint a = 1; // local variable
      uint b = 2;
      uint result = a + b;
      return result;
   }
}
```

### Calling a Function

To invoke a function somewhere later in the Contract, you would simply need to write the name of that function.

### Function Parameters
A function can take multiple parameters separated by comma.

### The return Statement

A Solidity function can have an optional return statement. This is required if you want to return a value from a function. This statement should be the last statement in a function.
```c++
pragma solidity ^0.5.0;

contract Test {
   function getResult() public view returns(uint product, uint sum){
      uint a = 1; // local variable
      uint b = 2;
      product = a * b;
      sum = a + b;
  
      //alternative return statement to return 
      //multiple values
      //return(a*b, a+b);
   }
}
```

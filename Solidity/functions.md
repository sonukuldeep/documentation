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


### Pure function
Pure functions ensure that they don't read or modify the state.<br> A function can be declared as pure. The following statements if present in the function are considered reading the state and compiler will throw warning in such cases.

    Reading state variables.

    Accessing address(this).balance or <address>.balance.

    Accessing any of the special variable of block, tx, msg (msg.sig and msg.data can be read).

    Calling any function not marked pure.

    Using inline assembly that contains certain opcodes.

Pure functions can use the revert() and require() functions to revert potential state changes if an error occurs.

Example;
```c++
pragma solidity ^0.5.0;

contract Test {
   function getResult() public pure returns(uint product, uint sum){
      uint a = 1; 
      uint b = 2;
      product = a * b;
      sum = a + b; 
   }
}
```

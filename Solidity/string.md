---
layout: home
parent: Solidity
title: String
---

## String
Solidity supports String literal using both double quote (") and single quote ('). <br>
It provides <ins>string</ins> as a data type to declare a variable of type String.
```c++
pragma solidity ^0.5.0;

contract SolidityTest {
   string data = "test";
}
```

In above example, "test" is a string literal and data is a string variable. 
* More preferred way is to use byte types instead of String as string operation requires more gas as compared to byte operation.
* Solidity provides inbuilt conversion between bytes to string and vice versa. 
* In Solidity we can assign String literal to a byte32 type variable easily. Solidity considers it as a byte32 literal.

```c++
pragma solidity ^0.5.0;

contract SolidityTest {
   bytes32 data = "test";
}
```

### Bytes to String Conversion

Bytes can be converted to String using string() constructor.

Syntax:
```c++
bytes memory bstr = new bytes(10);
string message = string(bstr);
```

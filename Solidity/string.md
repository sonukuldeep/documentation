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

### String to byte Conversion

String can be converted to bytes using bytes() constructor.

Syntax:
```c++
bytes memory stringToBytes = bytes("Hello world");
uint length = stringToBytes.length;
```

Example: 
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.7.0 <0.9.0;
 
contract LearnStrings {
    string greetings = "Hello world";
 
    function hello() public view returns (string memory) {
        return greetings;
    }
 
    function change(string memory _change) public payable {
        greetings = _change;
    }
 
    function getChar() public view returns (uint256) {
        bytes memory stringToBytes = bytes(greetings);
        return stringToBytes.length;
    }
}
```

Example 2

```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.7.0 <0.9.0;
 
contract FavouriteColor {
    string favouriteColor = "blue";
 
    function returnColor() public view returns (string memory) {
        return favouriteColor;
    }
 
    function changeString(string memory favColor) public payable {
        favouriteColor = favColor;
    }
 
    function charlen() public view returns (uint256) {
        bytes memory stringToByte = bytes(favouriteColor);
        return stringToByte.length;
    }
}
```
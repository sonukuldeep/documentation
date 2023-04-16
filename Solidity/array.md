---
layout: home
parent: Solidity
title: Array
---

# Array

## Table of Contents

## Array
* In Solidity, an array can be of compile-time fixed size or of dynamic size. 
* For storage array, it can have different types of elements as well. 
* In case of memory array, element type can not be mapping and in case it is to be used as function parameter then element type should be an ABI type.

### Array declaration
* Fixed array
* Dynamic array

#### Fixed array
```c++
type arrayName [ arraySize ];
```

This is called a single-dimension array. The arraySize must be an integer constant greater than zero and type can be any valid Solidity data type. For example, the following array is a 10-element array called balance of type uint
```c++
uint balance[10];
```

#### Dynamic array
To declare an array of dynamic size in Solidity, the programmer specifies the type of the elements as follows
```c++
type[] arrayName;

uint[] memory a;
```

### Initialisation
* Fixed array
```c++
uint balance[3] = [1, 2, 3];
uint balance[] = [1, 2, 3];
```

```c++
balance[2] = 5;
```
The above statement assigns element number 3rd in the array a value of 5. 

* Dynamic memory array
Dynamic memory arrays are created using new keyword.

```c++
uint size = 3;
uint balance[] = new uint[](size);
```
### Accessing Array Elements

```c++
uint salary = balance[2];
```

### Members

* length − length returns the size of the array. length can be used to change the size of dynamic array be setting it.

* push − push allows to append an element to a dynamic storage array at the end. It returns the new length of the array.


## Examples:

### Example: 1
```c++
pragma solidity ^0.5.0;

contract test {
   function testArray() public pure{
      uint len = 7; 
      
      //dynamic array
      uint[] memory a = new uint[](7);
      
      //bytes is same as byte[]
      bytes memory b = new bytes(len);
      
      assert(a.length == 7);
      assert(b.length == len);
      
      //access array variable
      a[6] = 8;
      
      //test array variable
      assert(a[6] == 8);
      
      //static array
      uint[3] memory c = [uint(1) , 2, 3];
      assert(c.length == 3);
   }
}
```

### Example: 2
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

contract LearnArray {
    uint256[] public myArray;
    uint256[] public myArray2; // empty array
    uint256[200] public fixedArray; // fixed sixed array
    uint256[] public numberList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
    
    // push it adds 1 or more element to the end of the array and returns the length

    function push(uint256 number) public payable {
        myArray.push(number);
    }

    // pop it remioves the last element from an array and returns that value
    function pop() public payable {
        myArray.pop();
    }

    function length() public view returns (uint256) {
        return myArray.length;
    }

    function remove(uint256 i) public payable {
        delete myArray[i];
        // remember length will not change. internally the value will be replaced by 0
    }

    function getValue(uint256 _n) public view returns (uint256) {
        if (_n >= myArray.length || _n < 0) {
            return 1000;
        } else {
            return myArray[_n];
        }
    }
}
```

### Exercise 3:
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

contract ArrayExercise {
    uint256[] public changeArray;

    constructor() {
        for (uint256 i = 1; i < 5; i++) {
            changeArray.push(i);
        }
        delete changeArray[1];
    }

    function removeElement() public payable {
        changeArray.pop();
    }

    function test() public payable {
        for (uint256 i = 1; i < 5; i++) {
            changeArray.push(i);
        }
    }

    function show() public view returns (uint256[] memory) {
        return changeArray;
    }

    function length() public view returns (uint256) {
        return changeArray.length;
    }
}
```


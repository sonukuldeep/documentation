---
layout: home
parent: Solidity
title: Loops
---

## Loops

Solidity supports all the necessary loops

* While loop
* Do... While loop
* For loop
* Loop control 

### while loop
Syntax:
```c++
while (expression) {
   Statement(s) to be executed if expression is true
}
```

### do... while loop
Syntax:
```c++
do {
   Statement(s) to be executed;
} while (expression);
```

### For loop
Syntax:
```c++
for (initialization; test condition; iteration statement) {
   Statement(s) to be executed if test condition is true
}
```

Example:-
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

contract LoopContract {
    uint256[] public numberList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

    function checkMultiples(uint256 _num, uint256 _nums)
        public
        pure
        returns (bool)
    {
        require(_num != 0 && _nums != 0, "Can't accept zero");
        if (_num % _nums == 0) {
            return true;
        } else {
            return false;
        }
    }

    function multipleChaecker(uint256 _number) public view returns (uint256) {
        uint256 countMultiple = 0;
        for (uint256 i = 0; i < numberList.length; i++) {
            if (checkMultiples(numberList[i], _number)) {
                countMultiple += 1;
            }
        }
        return countMultiple;
    }
}
```

<hr>

### Loop control
#### Break and Continue
##### Break
To handle all such situations, Solidity provides break and continue statements. These statements are used to immediately come out of any loop or to start the next iteration of any loop respectively.

Example:
```c++
while (true) {
         len++;
         j /= 10;
         if(j==0){
            break;   //using break statement
         }
      }
```

##### Continue
The continue statement tells the interpreter to immediately start the next iteration of the loop and skip the remaining code block.

Example:
```c++
while( n < 10){
         n++;
         if(n == 5){
            continue; // skip n in sum when it is 5.
         }
         sum = sum + n;
      }
```

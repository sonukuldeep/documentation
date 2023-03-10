---
layout: home
parent: Solidity
title: loops
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

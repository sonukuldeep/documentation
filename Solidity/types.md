---
layout: home
title: Types
parent: Solidity
---

## Types
While writing program in any language, you need to use various variables to store various information. Variables are nothing but reserved memory locations to store values. This means that when you create a variable you reserve some space in memory.

You may like to store information of various data types like character, wide character, integer, floating point, double floating point, boolean etc. Based on the data type of a variable, the operating system allocates memory and decides what can be stored in the reserved memory.
Value Types

Solidity offers the programmer a rich assortment of built-in as well as user defined data types. Following table lists down seven basic C++ data types

|Type|Keyword|Values|
| :---: | :---: | :---: |
|Boolean| bool | true/false|
|Integer | int/uint |Signed and unsigned integers of varying sizes.|
|Interger | int8 to int256 | Signed int from 8 bits to 256 bits. int256 is the same as int.|
|Integer|int8 to int256|Unsigned int from 8 bits to 256 bits. uint256 is the same as uint.|
|Fixed Point Numbers|fixed/unfixed|Signed and unsigned fixed point numbers of varying sizes.|
|Fixed Point Numbers|fixed/unfixed|Signed and unsigned fixed point numbers of varying sizes.|
|Fixed Point Numbers|fixedMxN| 	Signed fixed point number where M represents number of bits taken by type and N represents the decimal points. M should be divisible by 8 and goes from 8 to 256. N can be from 0 to 80. fixed is same as fixed128x18.|
|Fixed Point Numbers|ufixedMxN|Unsigned fixed point number where M represents number of bits taken by type and N represents the decimal points. M should be divisible by 8 and goes from 8 to 256. N can be from 0 to 80. ufixed is same as ufixed128x18.|

Note: You can also represent the signed and unsigned fixed-point numbers as fixedMxN/ufixedMxN where M represents the number of bits taken by type and N represents the decimal points. M should be divisible by 8 and goes from 8 to 256. N can be from 0 to 80.


### Address
Address holds the 20 byte value representing the size of an Ethereum address. An address can be used to get the balance using .balance method and can be used to transfer balance to another address using .transfer method.
```c++
address x = 0x212;
address myAddress = this;
if (x.balance < 10 && myAddress.balance >= 10) x.transfer(10);
```
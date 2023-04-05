---
layout: home
title: Solidity
has_children: true
---

# Solidity
Solidity is an object-oriented, high-level language for implementing smart contracts. Smart contracts are programs which govern the behaviour of accounts within the Ethereum state.

Solidity is a curly-bracket language designed to target the Ethereum Virtual Machine (EVM). It is influenced by C++, Python and JavaScript.

Solidity is statically typed, supports inheritance, libraries and complex user-defined types among other features.

With Solidity you can create contracts for uses such as voting, crowdfunding, blind auctions, and multi-signature wallets

## Reserved keywords

<table>
<tr>
<td>abstract</td>
<td>after</td>
<td>alias</td>
<td>apply</td>
</tr>
<tr>
<td>auto</td>
<td>case</td>
<td>catch</td>
<td>copyof</td>
</tr>
<tr>
<td>default</td>
<td>define</td>
<td>final</td>
<td>immutable</td>
</tr>
<tr>
<td>implements</td>
<td>in</td>
<td>inline</td>
<td>let</td>
</tr>
<tr>
<td>macro</td>
<td>match</td>
<td>mutable</td>
<td>null</td>
</tr>
<tr>
<td>of</td>
<td>override</td>
<td>partial</td>
<td>promise</td>
</tr>
<tr>
<td>reference</td>
<td>relocatable</td>
<td>sealed</td>
<td>sizeof</td>
</tr>
<tr>
<td>static</td>
<td>supports</td>
<td>switch</td>
<td>try</td>
</tr>
<tr>
<td>typedef</td>
<td>typeof</td>
<td>unchecked</td>
</tr>
</table>

## Comments
Solidity supports both C-style and C++-style comments, Thus −

    Any text between a // and the end of a line is treated as a comment and is ignored by Solidity Compiler.

    Any text between the characters /* and */ is treated as a comment. This may span multiple lines.

Example:-

The following example shows how to use comments in Solidity.
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >= 0.7.0 < 0.9.0;

contract LearnComments {

   function getResult() public view returns(uint){
      // This is a comment. It is similar to comments in C++
   
      /*
         * This is a multi-line comment in solidity
         * It is very similar to comments in C Programming
      */
      uint a = 1;
      uint b = 2;
      uint result = a + b;
      return result;
   }

}
```

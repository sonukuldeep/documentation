---
layout: home
title: Mapping
parent: Solidity
---

## Mapping 
Mapping is a reference type as arrays and structs. <br>
Following is the syntax to declare a mapping type.

```c++
mapping(_KeyType => _ValueType)
```
Where

    _KeyType − can be any built-in types plus bytes and string. No reference type or complex objects are allowed.

    _ValueType − can be any type.

### Considerations

* Mapping can only have type of storage and are generally used for state variables.

* Mapping can be marked public. Solidity automatically create getter for it.

Example:-1
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.7.0 <0.9.0;
 
contract LearnMapping {
    // create a map
    // address is the key, uint is the value. myMap is the datatype
    mapping(address => uint256) myMap;
 
    function setAddress(address _addr, uint256 _i) public {
        // assignment 
        myMap[_addr] = _i;
    }
 
    function getAddress(address _add) public view returns (uint256) {
        // using key to fetch value
        return myMap[_add];
    }
 
    function removeAddress(address _addr) public {
        // deleting value assigned to key
        delete myMap[_addr];
    }
}
```

Example:-2
```c++
pragma solidity ^0.5.0;

contract LedgerBalance {
   mapping(address => uint) public balances;

   function updateBalance(uint newBalance) public {
      balances[msg.sender] = newBalance;
   }
}
contract Updater {
   function updateBalance() public returns (uint) {
      LedgerBalance ledgerBalance = new LedgerBalance(); // inheritance
      ledgerBalance.updateBalance(10);
      return ledgerBalance.balances(address(this));
   }
}
```

Example:-3 Nested mapping
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.7.0 <0.9.0;
 
contract LearnNestedMapping {
    //struct declaration
    struct Movie {
        string title;
        string director;
    }
 
    // nested maping, here address and uint256 are keys
    mapping(address => mapping(uint256 => Movie)) myNestedMovie;
 
    function setNestedMovie(
        uint256 _i,
        string memory _title,
        string memory _director
    ) public {
        // observe how both the keys are used to assign the value here
        myNestedMovie[msg.sender][_i] = Movie(_title, _director);
    }
 
    // function returns Movie struct
    function getNestedMovie(uint256 _i) public view returns (Movie memory) {
        return myNestedMovie[msg.sender][_i];
    }
}
```

Example:-4 Mapping and struct
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.7.0 <0.9.0;
 
contract structMapAssignment {
// how mapping is assigned
mapping(uint256 => address) myMap;

function setmyMap(uint256 _id, address _addr) public {
    //assigned key value here
    myMap[_id] = _addr;
}

function deleteMyAddr(uint256 _i) public {
    // delete a value with associated key
    delete myMap[_i];
}

function checkValueOfMap(uint256 _i) public view returns (address) {
    // check the value with associated key
    return myMap[_i];

    // this is how struct is declared
    struct Movie {
        string title;
        string director;
    }
 
    // innitializing movie to struct Movie
    Movie movie;
 
    // struct mapping
    mapping(uint256 => Movie) movieStruct;
 
    function setMovie(
        string memory _name,
        string memory _director,
        uint256 _i
    ) public {
        // initializing movie with values
        movie = Movie(_name, _director);
        // assigning movie value to jey
        movieStruct[_i] = movie;
    }
 
    function getmovie(uint256 _i) public view returns (Movie memory) {
        // retun value of map
        return movieStruct[_i];
    }
}
```
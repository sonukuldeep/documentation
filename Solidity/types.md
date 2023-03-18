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


### Important types and data structure

Before we move on, let's update the code in our smart contract to be compatible with the latest version of Solidity at the time of writing this article. We can modify the first line in the smart contract code like this:

pragma solidity ^0.5.1;

Doing this will help us learn best practices for the current version of Solidity moving forward! Now let's address the warnings for the new version of solidity. First, modify the get() function to look like this:

function get() public view returns(string memory) {
    return value;
}

Note the memory distinction. We'll do the same for the set() function:

function set(string memory _value) public {
    value = _value;
}

Great! Now that we're up to date, let's talk about basic data types and data structures so that you can start implementing them into your own Ethereum smart contracts. We'll do this by first creating state variables of varying data types. First, let's look at some nice features of state variables provided by Solidity. Currently, we simply declare the value state variable, and the use the get() function to set it's value. There is a shortcut in solidity that makes this much easier. We can simply do this:

string public value;

This sets the visibility of the state variable to public, which means that anyone outside of the smart contract can read its value. When we do this, Solidity provides a value() function for free! Now we no longer need the get() function! We can also assign a default value to the state variable like this:

string public value = "myValue";

Now we no longer need to set this in the constructor function either! That really reduces the amount of code we have to write. We can also set this value as a constant that will never change like this:

string public constant value = "myValue";

Now that we've done this, we must remove the set() function because Solidity will not allow us to update this value since it is a constant.

That's an overview of the shortcuts Solidity provides for state variables. Now let's create some more state variables to examine some different data types available in Solidity. Just like the string state variable, we always declare the data type, then the visibility before declaring the variable name. First, we can create a boolean state variable like this:

bool public myBool = true;

This can be either true or false.Now we can create an unsigned integer like this:

Now we can create an integer like this:

int public myInt = 1;

Integers can be positive or negative, i.e., signed. If you don't want a number to be negative, you can create an unsigned integer like this:

uint public myUint = 1;

We can specify the number of bits for the number. The above example defaults to 256 bits. We can be explicit like this:

uint256 public myUint256 = 9999;

We can also restrict the value to 8 bits, like this:

uint8 public myUint8 = 8;

 
### Enums

Now let's go over some basic data structures in solidity. First, let's look at the Enum data structure, which are a way of keeping track of enumerated lists in Solidity. We can check against this list whenever you're writing smart contracts. Let's create an enum in the smart contract like this:
```c++
enum State { Waiting, Ready, Active }
```
Just as an example, this will help us keep track of the active state of the smart contract by providing Waiting, Ready, and Active options. We can check the current state of the smart contract like this:

### State public state;

Now, we can set the default state in the constructor:
```c++
constructor() public {
    state = State.Waiting;
}
```
Now, we can set the default state in the constructor:
```c++
constructor() public {
    state = State.Waiting;
}
```
We can update the current state to active like this:
```c++
function activate() public {
    state = State.Active;
}
```
And finally, we can check against the enum list to see if the state is currently active like this:
```c++
function isActive() public view returns(bool) {
    return state == State.Active;
}
```
Now the final smart contract code should look like this:
```c++
pragma solidity 0.5.1;

contract MyContract {
    enum State { Waiting, Ready, Active }
    State public state;

    constructor() public {
        state = State.Waiting;
    }

    function activate() public {
        state = State.Active;
    }

    function isActive() public view returns(bool) {
        return state == State.Active;
    }
}
```
That's an example of how you can use enums inside your smart contracts to track state! Just as another example, this is very useful for tracking the state of a crowdsale ICO smart contract that is open or closed. You can check that out in my other tutorial where I show you how to build a real world ICO.
Structs

Solidity allows you to define your own data types with Structs. You can basically model any kind of data you want with arbitrary attributes of varying data types. Let's look at how this works by creating a people struct:
```c++
struct Person {
    string _firstName;
    string _lastName;
}
```
We've modeled a person here that has a _firstName and _lastName. Notice that we're able to specify any data type that we want! We've used strings for both attributes here. We could add up to 17 different attributes here with any data type. For now, let's keep it simple and only use two attributes to model the person.

 
### Arrays

Now we need a place to store this person struct. Let's use an array for this! We can declare people array like this:
```c++
Person[] public people;
```
Notice we declare the type within the array, i.e., Person. We also set the visibility to public and assigned it to a state variable called people. This will provide us with a function that will allow us to access the people inside this array. I should mention though, that calling the people() function outside the smart contract will not return the entire array. Instead, the people() function will accept an index argument that will allow us to reference the person inside the array based upon that index, which is zero-based. For example, we can access the first person in the people array like this:
```c++
people(0)
```
Now let's create a way to add a person to this array. We'll create an addPerson() function like this:
```c++
function addPerson(string memory _firstName, string memory _lastName) public {
    people.push(Person(_firstName, _lastName));
    peopleCount += 1;
}
```
This function will accept the arguments for the person struct attributes, then instantiate a new person and add it to the people array with the push function. It also increments the peopleCount state variable by 1. We can implement that state variable in the smart contract like this:
```c++
uint256 public peopleCount;
```
We'll use this value as a counter cache. Remember how I said that you can't return the entire people array with the people() function? Knowing how many people are inside this array will help us know how many times we must call the people() function to get each person.

Now the completed smart contract code should look like this:
```c++
pragma solidity 0.5.1;

contract MyContract {
    Person[] public people;

    uint256 public peopleCount;

    struct Person {
        string _firstName;
        string _lastName;
    }

    function addPerson(string memory _firstName, string memory _lastName) public {
        people.push(Person(_firstName, _lastName));
        peopleCount += 1;
    }
}
```
 
### Mappings

Solidity provides a data structure called a mapping which allows us to store key-value pairs. This structure acts much like an associative array or a hash table in other functions. We can declare a mapping in the smart contact like this:

mapping(uint => Person) public people;

This will be a mapping where we store person structs. It will replace the people array we used in the previous example. The key will be an unsigned integer, and the value will be a person struct. We'll treat the key like a database id. We can update the person struct to keep track of that id like this:

struct Person { uint _id; string _firstName; string _lastName; }

Now we can modify the addPerson() function to update the people mapping like this:
```c++
function addPerson(string memory _firstName, string memory _lastName) public {
    peopleCount += 1;
    people[peopleCount] = Person(peopleCount, _firstName, _lastName);
}
```
This uses the peopleCount counter cache to create an id for the person. Then it instantiates a new person struct with the id and the passed in attributes. It then adds this to the people mapping. The completed smart contract code should look like this:
```c++
pragma solidity 0.5.1;

contract MyContract {
    uint256 peopleCount = 0;

    mapping(uint => Person) public people;

    struct Person {
        uint _id;
        string _firstName;
        string _lastName;
    }

    function addPerson(string memory _firstName, string memory _lastName) public {
        peopleCount += 1;
        people[peopleCount] = Person(peopleCount, _firstName, _lastName);
    }
}
```

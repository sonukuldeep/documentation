---
title: Enums
layout: home
parent: Typescript Fundamentals
---

# Basics
 
```tsx
enum VehicleType {
 PedalCycle,
 MotorCycle,
 Car,
 Van,
 Bus,
 Lorry
}
```

* Enumerations represent a collection of named elements that you can use to avoid littering your program with hard-coded values.
* By default, enumerations are zero based although you can change this by specifying the first value, in which case numbers will 
increment from value you set. 
* You can opt to specify values for all identifiers if you wish to too.

## Emum with string
```tsx
 enum CardinalDirections {
  North = 'North',
  East = "East",
  South = "South",
  West = "West"
};
// logs "North"
console.log(CardinalDirections.North);
// logs "West"
console.log(CardinalDirections.West);
```

## Const enum
```tsx
const enum Light {
    Red,
    Green,
    Blue
}
```tsx

* const enum references are replaced by inline codes. For example, console.log(Light.Red) is compiled as console.log(0 /* Red */).
* If there is no JavaScript object that associates with const enum is generated at run time, it is not possible to loop over the const enum values.

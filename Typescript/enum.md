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
* You can opt to specify values for all identifiers if you wish to.

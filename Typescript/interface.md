---
title: Interface
layout: home
parent: Typescript Fundamentals
---

# examples

```tsx
Interface InumberArray {
 myVar: number[];
}


## Extends
```tsx
interface Animal {
  name: string;
  age: number;
  eat: (food: string) => void;
}

interface Dog extends Animal {
  breed: string;
  bark(): void;
}
```

Eat is a function that takes food as an argument and does not return a value
Bark is also a function that doesn't take any argument and does not return a value
Different ways to write a function in type script

### Extend with type

```tsx
type Fruit = {
  sweet: boolean
}

interface Vegetable {
  berry: boolean
}

interface Tomato extends Fruit, Vegetable {
  season: boolean
}
```

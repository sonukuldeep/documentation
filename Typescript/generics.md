---
title: Generics 
layout: home
parent: Typescript Fundamentals
---

# Generics
Generics allow you to create reusable components that work with a variety of data types.


You can use generics to define an array of a specific type. For example, you can define an array of strings like this:

```tsx
const names: Array<string> = ['Alice', 'Bob', 'Charlie'];
```

This is equivalent to using the shorthand syntax for arrays in TypeScript:

```tsx
const names: string[] = ['Alice', 'Bob', 'Charlie'];
```

### Function

To define a generic function called identity that takes a type parameter and returns the same value it received as an argument, you would write:

```tsx
function identity<T>(arg: T): T {
  return arg;
}
```

Generics functions to create reusable code that can work with a variety of data types. For example, you can define a generic function called reverse that takes an array of any type and returns the reversed array:

```tsx
function reverse<T>(arr: T[]): T[] {
  return arr.reverse();
}
```

Here, the type parameter T can be any type, and we're using it to specify the type of the array that the function takes and returns.

### Interface
You can use generics with interfaces to define flexible and reusable types. For example, you can define a generic interface called Box that takes a type parameter T and has a single property called content of type T:

```tsx
interface Box<T> {
  content: T;
}
```

This interface can be used to define a variety of boxes that contain different types of content. For example, you can define a box that contains a string like this:

```tsx
const stringBox: Box<string> = { content: 'Hello, World!' };
```

And you can define a box that contains a number like this:
```tsx
const numberBox: Box<number> = { content: 42 };
```

### Examples
```tsx
// Ex: 1
const makeFetch = <T>(url: string): Promise<T> => {
  return fetch(url).then((res) => res.json())
}

makeFetch<{ firstName: string }>("/api").then((res) => console.log(res))


// Ex: 2
const addIdToObject = <T>(obj: T) => {
  return { ...obj, id: "123" }
}

const result = addIdToObject({ firstname: "Hello" })

// Ex: 3
type GetPromiseReturnType<T extends (...args: any) => any> = Awaited<
  ReturnType<T>
>

// this works for variables awaiting a promise
type Return1 = Awaited<Promise<string>>

// Returntype exist for a function
type Return2 = ReturnType<() => number>

type Result = GetPromiseReturnType<() => Promise<{ firstname: string }>>
```
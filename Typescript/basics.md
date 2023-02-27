---
title: Typescript basics 
layout: home
parent: Typescript Fundamentals
---

# Basics

## Common stuff

```ts
const name: string = 'your name'
const fun: (a: number, b: number) => boolean = (a,b) => {return true}
```

## Interface

```ts
interface IProps {
    name: string
    age: number
}
```

### Extends

```ts
interface IFunProps {
    fun: (a: string) => void //function type
}

interface IProps extends IFunProps {
    name: string
    age: number
}
```

### Interface overload

```ts
interface IProps {
    name: string
    age: number
}

interface IProps {
    fun: (a: string) => void
}
```

This is same as below

```ts
interface IProps {
    name: string
    age: number
    fun: (a: string) => void
}
```

## Type

```ts
type Props = {
    name: string
    age: number
    fun: (a: string) => void
}
```

### Union

 ```ts
 type USAddress = {
    street: string
    state: string
 }
 type CanadaAddress = {
    street: string
    province: street
 }
 type Address = CanadaAddress | USAddress
 ```
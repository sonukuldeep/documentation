---
title: Typescript basics 
layout: home
parent: Typescript Fundamentals
---

# Basics

## Common stuff

```tsx
const name: string = 'your name'

const fun:({name: string}) => void = ({name}) => {}
or
const fun = ({name}:{name: string}): void => {}

const fun: (a: number, b: number) => boolean = (a,b) => {return true}
or
const fun: (a: number, b: number): boolean => { return true }
```

## Interface

```tsx
interface IProps {
    name: string
    age: number
}
```

### Extends

```tsx
interface IFunProps {
    fun: (a: string) => void //function type
}

interface IProps extends IFunProps {
    name: string
    age: number
}
```

### Interface overload

```tsx
interface IProps {
    name: string
    age: number
}

interface IProps {
    fun: (a: string) => void
}
```

This is same as below

```tsx
interface IProps {
    name: string
    age: number
    fun: (a: string) => void
}
```

## Type

```tsx
type Props = {
    name: string
    age: number
    fun: (a: string) => void
}
```

### Union

 ```tsx
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
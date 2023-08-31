---
title: Declare module
layout: home
parent: Typescript Fundamentals
---

## Declare module

The `declare module` syntax in TypeScript is used to extend or add types to existing modules, especially when working with third-party libraries. Here are a few more examples of how you might use the `declare module` syntax:

**Example 1: Extending a Third-Party Library**

Suppose you're working with a library called "awesome-library" that doesn't have type definitions built-in. You can use `declare module` to add your own type definitions for the library's components:

```typescript
declare module 'awesome-library' {
    export function doSomething(value: string): void;
    export function doAnotherThing(): number;
}
```

**Example 2: Extending a Module with Interfaces**

Let's say you're using the "axios" library for making HTTP requests and you want to extend the types of its response data:

```typescript
import axios, { AxiosResponse } from 'axios';

declare module 'axios' {
    interface AxiosResponse<T = any> {
        customData: T;
    }
}

// Now you can use your customData property in responses
axios.get('/api/data').then((response: AxiosResponse<{ customData: number }>) => {
    const data = response.customData;
});
```

**Example 3: Extending a Module with Enums**

If you're using an enum from a library and want to add your own values:

```typescript
declare module 'my-enums' {
    export enum Colors {
        Red = 'red',
        Green = 'green',
        Blue = 'blue',
        CustomColor = 'custom',
    }
}
```

**Example 4: Extending the Window Object**

You can extend the global `window` object to add new properties:

```typescript
interface CustomWindow extends Window {
    myApp: {
        version: string;
    };
}

declare global {
    interface Window {
        myApp: {
            version: string;
        };
    }
}

// Now you can access your custom property on the window object
window.myApp.version = '1.0.0';
```

These examples demonstrate different scenarios where you might use `declare module` to add, extend, or modify types within existing modules or global objects. It's a powerful feature of TypeScript that allows you to provide better type information and integrate with third-party libraries more effectively.

## Extend type for mui color palette
```js
// Augment the palette to include a violet color
declare module '@mui/material/styles' {
  interface Palette {
    violet: Palette['primary'];
  }

  interface PaletteOptions {
    violet?: PaletteOptions['primary'];
  }
}
```

The syntax you're seeing is TypeScript's way of referencing and reusing types within the same interface definition. Let me break down that specific part for clarity:

```typescript
customNeutral: Palette['primary'];
```

In this line, you're defining the `customNeutral` palette to be the same type as the `primary` palette. Here's what it means in more straightforward terms:

- The `Palette` interface represents a color palette in Material-UI.
- The `Palette['primary']` syntax is a way to refer to the type of the `primary` property within the `Palette` interface.

So, by using `customNeutral: Palette['primary']`, you're saying that `customNeutral` will have the same type as the `primary` palette. This means that any properties you define within `customNeutral` will need to match the structure of the `primary` palette.

For example, in your code:

```typescript
customNeutral: {
    light: grey[50],
    main: grey[200],
    dark: grey[700],
    contrastText: grey[900],
},
```

You're structuring `customNeutral` to have the same properties (`light`, `main`, `dark`, `contrastText`) as the `primary` palette.

If you find this syntax confusing, you can make it more explicit by directly referencing the properties you want instead of using `Palette['primary']`. For instance:

```typescript
customNeutral: {
    light: grey[50],
    main: grey[200],
    dark: grey[700],
    contrastText: grey[900],
} as PaletteColor,
```

Here, I've used `PaletteColor` to explicitly state the type, but you can replace it with the exact type that the `primary` palette properties have. This makes it clearer what you're defining for `customNeutral`.

Remember, this syntax is specific to TypeScript and interfaces and is used to reuse and reference type definitions within an interface or type declaration.
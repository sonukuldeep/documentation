---
layout: home
title: Typescript React
parent:
---

# React props with ts
```tsx
// Declaring type of props - see "Typing Component Props" for more examples
type AppProps = {
  message: string;
};

// Easiest way to declare a Function Component; return type is inferred.
const App = ({ message }: AppProps) => <div>{message}</div>;

// you can choose annotate the return type so an error is raised if you accidentally return some other type
const App = ({ message }: AppProps): JSX.Element => <div>{message}</div>;

// you can also inline the type declaration; eliminates naming the prop types, but looks repetitive
const App = ({ message }: { message: string }) => <div>{message}</div>;
```

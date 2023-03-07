---
layout: home
title: Typescript React
parent: Typescript Fundamentals
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

## useRef

In TypeScript, useRef returns a reference that is either read-only or mutable, depends on whether your type argument fully covers the initial value or not. Choose one that suits your use case.
Option 1: DOM element ref

To access a DOM element: provide only the element type as argument, and use null as initial value. In this case, the returned reference will have a read-only .current that is managed by React. TypeScript expects you to give this ref to an element's ref prop:

```tsx
function Foo() {
  // - If possible, prefer as specific as possible. For example, HTMLDivElement
  //   is better than HTMLElement and way better than Element.
  // - Technical-wise, this returns RefObject<HTMLDivElement>
  const divRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    // Note that ref.current may be null. This is expected, because you may
    // conditionally render the ref-ed element, or you may forgot to assign it
    if (!divRef.current) throw Error("divRef is not assigned");

    // Now divRef.current is sure to be HTMLDivElement
    doSomethingWith(divRef.current);
  });

  // Give the ref to an element so React can manage it for you
  return <div ref={divRef}>etc</div>;
}
```

If you are sure that divRef.current will never be null, it is also possible to use the non-null assertion operator !:

const divRef = useRef<HTMLDivElement>(null!);
// Later... No need to check if it is null
doSomethingWith(divRef.current);

Note that you are opting out of type safety here - you will have a runtime error if you forget to assign the ref to an element in the render, or if the ref-ed element is conditionally rendered.
Tip: Choosing which HTMLElement to use

Option 2: Mutable value ref

To have a mutable value: provide the type you want, and make sure the initial value fully belongs to that type:

```tsx
function Foo() {
  // Technical-wise, this returns MutableRefObject<number | null>
  const intervalRef = useRef<number | null>(null);

  // You manage the ref yourself (that's why it's called MutableRefObject!)
  useEffect(() => {
    intervalRef.current = setInterval(...);
    return () => clearInterval(intervalRef.current);
  }, []);

  // The ref is not passed to any element's "ref" prop
  return <button onClick={/* clearInterval the ref */}>Cancel timer</button>;
}
```

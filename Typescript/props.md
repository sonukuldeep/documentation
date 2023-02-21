---
title: Props in FC 
layout: home
parent: Typescript Fundamentals
---

### Props in typescript

Functional component
```tsx
import React from 'react';

interface Props {
  name: string;
  age: number;
}

const MyComponent: React.FC<Props> = ({ name, age }) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>You are {age} years old.</p>
    </div>
  );
};

export default MyComponent;
```

Class component
```tsx
import React from 'react';

interface Props {
  name: string;
}

class MyComponent extends React.Component<Props> {
  handleClick = (): void => {
    console.log(`Hello, ${this.props.name}!`);
  }

  render() {
    return (
      <div>
        <h1>Hello, {this.props.name}!</h1>
        <button onClick={this.handleClick}>Click me!</button>
      </div>
    );
  }
}

export default MyComponent;
```
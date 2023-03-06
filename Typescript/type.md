---
title: Types
layout: home
parent: Typescript Fundamentals
---


# Basic

Ex-1
```tsx
type typename = {
name: string
}
```

Ex-2
```tsx
type IdProps = {
  id: string,
  display: string
}

const list: IdProps[] = [
  {
    id: 'foo',
    display: 'Foo Select'
  },
  {
    id: 'bar',
    display: 'Bar Select'
  },
]
```

Ex-3
```tsx
type CreditCard = {
  number: number;
  cardholder: string;
  expirationDate: Date;
  secutiryCode: number;
};

type DebitCard = {
  number: number;
  cardholder: string;
  expirationDate: Date;
  secutiryCode: number;
};

type PaymentMethod = CreditCard | DebitCard;
```

Ex-4
```tsx
type Fruit = {
    sweet: boolean
}

type Vegetable = {
    berry: boolean
}

type Tomato = Fruit & Vegetable
```

Ex-5
```tsx
type Book = {
  title: string;
  price: number;
};

type Author = {
  name: string;
  email: string;
  books: Book[];
};
```

---
title: Snippets
layout: home
has_children: true
---

![hero](../assets/images/0991248287.PT02_1200x1200.webp)

# Useful snippets and links

### Next js with styled-components
```bash
npx create-next-app --typescript --example with-styled-components my-app
```

<hr>

### Next js with sass and open-props
```bash
npx create-next-app --typescript my-app
cd my-app
npm install -D open-props sass
```

<hr>

### How to detect click outside React component ?

[source](https://www.geeksforgeeks.org/how-to-detect-click-outside-react-component/)

Same code in typescript

```typescript
function useOutsideAlerter(ref: React.RefObject<HTMLElement>) {
  useEffect(() => {
    function handleOutsideClick(event: MouseEvent) {
      if (ref.current && !ref.current.contains(event.target as Node)) {
        alert("you just clicked outside of box!");
      }
    }

    document.addEventListener("click", handleOutsideClick);
    return () => document.removeEventListener("click", handleOutsideClick);
  }, [ref]);
}
```

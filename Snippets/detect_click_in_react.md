---
layout: home
parent: Snippets
title: Handle click outside component
---

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

If there is click event inside click event then make sure to fire *event.stopPropagation()*
to prevent click event in 2 or more places
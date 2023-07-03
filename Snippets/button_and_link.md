---
parent: 'Snippets'
layout: 'home'
title: 'Button Link'
---

## Open link js
```js
<p>Check out <a href="https://www.freecodecamp.org/" target="_blank" rel="noopener noreferrer">freeCodeCamp</a>.</p>
```

## Open link React js
```jsx
import React from 'react';

const OpenLink = () => {
  const handleClick = () => {
    window.open('https://example.com', '_blank', 'noopener,noreferrer');
  };

  return (
    <a href="#" onClick={handleClick} rel="noopener noreferrer">Open Link</a>
  );
};

export default OpenLink;
```

## Open link in react with button
```jsx
import React from 'react';

const OpenLinkButton = ({ url }) => {
  const handleClick = () => {
    window.open(url, '_blank', 'noopener,noreferrer');
  };

  return (
    <button onClick={handleClick}>Open Link</button>
  );
};

export default OpenLinkButton;
```
---
title: Event bubbling in JavaScript
layout: home
parent: JavaScript Fundamentals
---

### What is event bubbling in JavaScript?

Event bubbling is a mechanism in JavaScript where an event, such as a click event, is first handled by the element that the event was triggered on, and then it is passed up the DOM tree to the parent element, and so on. This allows you to attach event listeners to parent elements that can handle events on their child elements.

Here's an example of event bubbling:

```html
<div id="parent">
  <div id="child">
    <div id="grandchild">Click me!</div>
  </div>
</div>
```

```js
const grandChild = document.getElementById("grandchild");
grandChild.addEventListener("click", function(event) {
  console.log("Grandchild clicked!");
});
const child = document.getElementById("child");
child.addEventListener("click", function(event) {
  console.log("Child clicked!");
});
const parent = document.getElementById("parent");
parent.addEventListener("click", function(event) {
  console.log("Parent clicked!");
});
```

In this example, when the user clicks on the grandchild element, the event will be first handled by the grandchild element's event listener and logs "Grandchild clicked!" to the console. Then, the event will bubble up to the parent elements, the child and parent element's event listener, where it will also be handled by each event listener respectively. So the event listener of the child element will log "Child clicked!" and the event listener of the parent element will log "Parent clicked!" to the console.

It's worth noting that when an event is handled by an element's event listener, it will be passed up the DOM tree to its parent element's event listener regardless of whether the event was handled or not. However, you can stop the event bubbling by calling the <u>event.stopPropagation()</u> method which will prevent the event from being passed up the DOM tree.

It's also important to note that the order of event handling is in the order of the DOM tree hierarchy, it starts from the innermost element to the outermost element.

Event bubbling allows you to handle events on multiple elements by using a single event listener on a parent element. This can be useful for reducing the number of event listeners in your code and handling events on multiple elements with similar behavior.

<u><i>source chat gpt</i></u>
---
excalidraw-plugin: parsed
tags:
  - excalidraw
excalidraw-open-md: true
---
## What is the difference between `useMemo` and `useCallback` ?

In React, `useMemo` and `useCallback` are two popular hooks that help optimize performance by memoize values and functions.

**useMemo**

useMemo is a hook that memoizes a value, which means it caches the result of a function so that its not recalculated on every render. This hook take two arguments.

1. A function that returns a value to be memoized
2. An array of dependencies.

The function is only executed when the dependencies change, and the memoized value is returned. If the dependencies don't change the cached value is returned

Example :

```js
import { useMemo } from 'react';

function Example() {
  const count = 5;
  const doubleCount = useMemo(() => count * 2, [count]);

  return <div>Double count: {doubleCount}</div>;
}
```

In the above example, `doubleCount` is memoized and only recalculated when the `count` changes.

---

**useCallback**

`useCallback` is a hook that memoizes a function, which means it caches a function so that it's not recreated on every render. The hook takes two arguments:

1. A function to be memoized
2. An array of dependecies.

The function is only recreated when the dependencies change, and the memoized function is returned. If the dependencies don't change, the cached function is returned

Example :

```js
import { useCallback } from 'react';

function Example() {
  const handleClick = useCallback(() => {
    console.log('Button clicked!');
  }, []);

  return <button onClick={handleClick}>Click me!</button>;
}

```

In this example, `handleClick` is memoized and only recreated when the dependencies change (in this case, none)

### When to use 

| useMemo                                                                    | useCallback                                                                                            |
| -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| when you have an expensive computation that depends on some props or state | when you have a function that's passed as a prop to a child component                                  |
| when you want to memoize a value that's used in your component             | when you want to prevent unnecessary re-renders of a child component when the parent component changes |
### In Summary

`useMemo` memoizes a value, optimizing expensive computations.

`useCallback` memoizes a function, preventin unnecessary re-renders of component that rely on a function prop.


## Binary Search

![[React Interview Questions.svg]]






%%
# Excalidraw Data

## Text Elements
l ^2lGbLKpa

r ^h8bTWhaP

mid = (l + r) // 2 ^ycjisHAQ

%%
## Drawing
```compressed-json
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
```
%%
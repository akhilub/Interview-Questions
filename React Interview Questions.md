---
excalidraw-plugin: parsed
tags:
  - excalidraw
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

==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
l ^2lGbLKpa

r ^h8bTWhaP

mid = (l + r) // 2 ^ycjisHAQ

%%
## Drawing
```compressed-json
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=
```
%%
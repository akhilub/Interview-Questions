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
%%
## Drawing
```compressed-json
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

gBMZKaUHdcOTxAJPIAA=
```
%%
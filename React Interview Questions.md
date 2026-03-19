
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
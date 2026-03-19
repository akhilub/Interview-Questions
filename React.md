

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

**useCallback**

`useCallback` is a hook that memoizes a function, which means it caches a function so that it's not recreated on every render. The hook takes two arguments:

1. A function to be memoized
2. An array of dependecies.

The function is only recreated when the dependecies chan

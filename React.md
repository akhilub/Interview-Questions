

## What is the difference between `useMemo` and `useCallback` ?

In React, `useMemo` and `useCallback` are two popular hooks that help optimize performance by memoize values and functions.

**useMemo**

useMemo is a hook that memoizes a value, which means it caches the result of a function so that its not recalculated on every render. This hook take two arguments.

1. A function that returns a value to be memoized
2. An array of dependencies.

The function is only execute
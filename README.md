# Unnecessary useEffect Re-renders in React

This example demonstrates a common issue in React where the `useEffect` hook is causing unnecessary re-renders due to incorrect dependency management.

## Bug
The `useEffect` hook inside `MyComponent` runs after every render because the `count` variable is included in the dependency array `[count]`.  This causes the `console.log` to print on each click, even though it's not essential for functionality.   This can lead to performance issues, especially with more complex components and state updates.

## Solution
The solution is to remove the `count` variable from the dependency array if the side-effect does not depend on the updated value of `count`.  If you want to run the effect only after initial render, pass an empty array `[]` as the dependency array. If you need to run the effect only after certain state changes you can specify these states as dependency. 
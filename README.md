# ReactJS-Hooks

ReactJS Hooks Syntactical Walkthrough

## useState

Definition: The useState hook allows you to add state to a functional component. It returns a state variable and a function to update that state.

```bash
import React, { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

## useEffect

Definition: The useEffect hook lets you perform side effects in your component, such as fetching data, directly interacting with the DOM, or using timers. It runs after the render is committed to the screen.

```bash
import React, { useEffect, useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]); // Only re-run the effect if count changes

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );

```

## useContext

Definition: The useContext hook allows you to access the value of a context within a functional component, bypassing the need for prop drilling.

```bash
import React, { useContext } from 'react';

const MyContext = React.createContext();

function Example() {
  const value = useContext(MyContext);

  return <div>{value}</div>;
}

function App() {
  return (
    <MyContext.Provider value="Hello, World!">
      <Example />
    </MyContext.Provider>
  );
}
```

## useReducer

Definition: The useReducer hook is used for managing more complex state logic that involves multiple sub-values or when the next state depends on the previous one. It works similarly to useState but uses a reducer function.

```bash
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Example() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </div>
  );
}
```

## useCallback

Definition: The useCallback hook returns a memoized version of the callback function that only changes if one of the dependencies has changed. It's useful to optimize performance by preventing unnecessary re-creations of functions.

```bash
import React, { useCallback, useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => {
    setCount(count + 1);
  }, [count]); // Only re-create the function if count changes

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={increment}>Click me</button>
    </div>
  );
}
```

## useMemo

Definition: The useMemo hook returns a memoized value that only recomputes if one of the dependencies has changed. It can improve performance by preventing expensive calculations on every render.

```bash
import React, { useMemo, useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  const expensiveCalculation = useMemo(() => {
    return count * 2; // Assume this is an expensive calculation
  }, [count]); // Only re-calculate if count changes

  return (
    <div>
      <p>Expensive Calculation: {expensiveCalculation}</p>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

## useRef

Definition: The useRef hook returns a mutable ref object whose .current property is initialized to the passed argument. This ref object persists for the lifetime of the component and can be used to access DOM elements or store mutable values.

```bash
import React, { useRef } from 'react';

function Example() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus the input</button>
    </div>
  );
}
```

## useLayoutEffect

Definition: The useLayoutEffect hook is similar to useEffect, but it fires synchronously after all DOM mutations. This is useful for reading layout and synchronously re-rendering.

```bash
import React, { useLayoutEffect, useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useLayoutEffect(() => {
    console.log('useLayoutEffect');
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

## Author

### Praabindh Pradeep

#### MERN Full Stack Web Developer

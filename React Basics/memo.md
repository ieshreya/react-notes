### What is memo?
If explained in one line, 
> Pure components : class components :: memo : functional components

- what pure components is to class components, memo is to functional components
- Using `memo` will cause React to skip rendering a component if its props have not changed.

This can improve performance.

<iframe width="560" height="315" src="https://www.youtube.com/embed/7TaBhrnPH78" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- below notes taken from w3 schools:
---

## Problem

In this example, the `Todos` component re-renders even when the todos have not changed.

### Example:

`index.js`:

```jsx
import { useState } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState(["todo 1", "todo 2"]);

  const increment = () => {
    setCount((c) => c + 1);
  };

  return (
    <>
      <Todos todos={todos} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));
```

`Todos.js`:

```jsx
const Todos = ({ todos }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
    </>
  );
};

export default Todos;
```

[Run Example »](https://www.w3schools.com/react/showreact.asp?filename=demo2_react_memo1)

When you click the increment button, the `Todos` component re-renders.

If this component was complex, it could cause performance issues.

## Solution

To fix this, we can use `memo`.

Use `memo`to keep the `Todos` component from needlessly re-rendering.

Wrap the `Todos` component export in `memo`:

### Example:

`index.js`:

```jsx
import { useState } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState(["todo 1", "todo 2"]);

  const increment = () => {
    setCount((c) => c + 1);
  };

  return (
    <>
      <Todos todos={todos} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));
```

`Todos.js`:

```jsx
import { memo } from "react";

const Todos = ({ todos }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
    </>
  );
};

export default memo(Todos);
```

[Run Example »](https://www.w3schools.com/react/showreact.asp?filename=demo2_react_memo2)

Now the `Todos` component only re-renders when the `todos` that are passed to it through props are updated.
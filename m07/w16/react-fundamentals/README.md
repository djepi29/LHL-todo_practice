# M07-W16 | React Fundamentals

## Topics to cover

- [x] 0. Component-based Frameworks
    - [x] Component-based real life examples
    - [x] Convert interface designs to component-based UI

- [x] 1. What is React?
  - [x] Anatomy of a React Component
  - [x] React without JSX
  - [x] React.createElement
  - [x] ReactDOM.render
  - [x] The role of Babel

- [x] 2. Create a project with Create React App

- [x] 3. JSX
  - [x] Imperative vs Declarative
  - [x] JSX syntax, rules and errors

- [x] 4. Components
  - [x] Creating a Functional Component
  - [x] Importing a component for use by other components
  - [x] Fragments

- [x] 5. Event Handlers
- [x] 6. Props
- [x] 7. State
- [x] 8. Controlled Components

## Extra Content

- [ReactJS Docs](https://reactjs.org/docs/getting-started.html)
- [MDN: Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
- [npx VS. npm](https://stackoverflow.com/questions/50605219/difference-between-npx-and-npm)

### 0. Create React App
---

We can use the following package: https://create-react-app.dev/

To install a react project that is ready to go. We just have to execute the following command in terminal:

```terminal
$ npx create-react-app my-project-folder-name
```

### 1. React
---

- From the landing page of [React](https://reactjs.org/):
  > A JavaScript library for building user interfaces
- Open source project maintained by Facebook
- React is built around the concept of managing data
  - Changes to the underlying data result in changes to the UI
  - In React, state === data
- Component-based: UI is composed of small pieces
- Declarative: We describe the final outcome of our code and not the step-by-step process to achieve that result

### 2. JSX
---

- It stands for JavaScript XML.
- To describe what the UI should look like.
- We will have to these rules to write JSX correctly:

#### Rule 0

`import React from "react";` AND `export default _______` <- your function name here

#### Rule 1 - All Tags MUST be closed.

```jsx
<div>
  {/* ... Components or other HTML in here ...  which are also closed correctly! */}
</div>
```

Or

```jsx
<ListItem />
```

#### Rule 2 - Child tags MUST close before the parent.

```jsx
<ul>
  <li>Child1</li>
  <li>Child2</li>
  <li>Child3</li>
  <li>Child4</li>
</ul>
```

#### Rule 3 - All JSX expressions MUST have a parent (or root) element.

```jsx
return (
  <div>
    <span>Name: Chuck Norris</span>
    <p>Chuck Norris threw a grenade and killed 50 people, then it exploded.</p>
  </div>
);
```

### 3. Components
---

- Components are the building blocks of a webpage (eg. search input, navigation bar, contact us form)
- Ideally, components should be reusable (which means that their state should be passed into them via props rather than maintaining their own state)
- Deciding which DOM elements become components and which don't is a skill that comes with practice and experience
- We will be building all of our components using functions
- The functions return value contains a mixture of HTML and JS; React calls this `JSX`

```jsx
// basic component
import React from 'react';

function MyComponent() {
  return (
    <div className="my-component">
      <h1>Hello World</h1>
    </div>
  );
}

export default MyComponent;
```

### 4. Event Handlers
---

- Functions that are extecuted when some event has raised.
- Don't forget to pass a function as the event handler, not a funciton call.

```jsx
// basic component
import React from 'react';

const CounterButton = () => {
  let [counter, setCounter] = useState(0);

  return (
    <div className="counterButton">
      <h2>The value of the counter is {counter}</h2>
      <button
        onClick={() => {
          setCounter(counter + 1);
        }}
      >
        Increase
      </button>
    </div>
  );
};

export default MyComponent;
```

### 5. State
---

- State (data) is created in a component by using the `State` hook (`useState`)
- `useState` takes an initial value for state which will be used on the first render
- `useState` returns the current value of state and a function (a way to set the value)

```js
// it's common to destructure the return value from useState
const [username, setUsername] = useState('');
```

#### NOTE: We need to use `useState` to keep track of our data so that React will know when changes occur

### 6. Passing Props
---

- Child components can be passed pieces of state (data) from their parent component
- These props are accepted in the child component as an argument (usually called `props`)

```jsx
// in parent component
import MyComponent from './components/MyComponent.jsx';

// inside the parent's return
<MyComponent studentName="Alice"></MyComponent>;

// inside child component
const MyComponent = props => {
  console.log(props); // we will see an object with keys studentName.
  return (
    <div>
      <h1>Hello {props.studentName}!</h1>
    </div>
  );
};
```

- Props are not limited to JS primitives and data structures; you can also pass behaviour from parent-to-child in the form of functions


# React Mastery: Understanding Core Concepts
 Dive deep into React's fundamental concepts with detailed explanations and practical examples. Master components, JSX, hooks, and more to level up your React skills


# React Concepts Explained

## Table of Contents

1. [Introduction to Components](#1-introduction-to-components)
2. [JSX](#2-jsx)
3. [Props](#3-props)
4. [Composition and Fragments](#4-composition-and-fragments)
5. [Keys](#5-keys)
6. [Rendering and Virtual DOM](#6-rendering-and-virtual-dom)
7. [Event Handling](#7-event-handling)
8. [State and useState Hook](#8-state-and-usestate-hook)
9. [Controlled Components](#9-controlled-components)
10. [React Hooks](#10-react-hooks)
11. [Pure Components and Strict Mode](#11-pure-components-and-strict-mode)
12. [Effects and useEffect Hook](#12-effects-and-useeffect-hook)
13. [Refs and useRef Hook](#13-refs-and-useref-hook)
14. [Context](#14-context)
15. [Portals](#15-portals)
16. [Suspense](#16-suspense)
17. [Error Boundaries](#17-error-boundaries)


## 1. Introduction to Components

Components are the building blocks of every React app. They allow us to create reusable and modular pieces of UI. In React, components can be functional or class-based.

Example:

```jsx
// Functional component
const Button = () => {
  return <button>Click Me</button>;
};

// Class-based component
class Input extends React.Component {
  render() {
    return <input type="text" />;
  }
}
```

## 2. JSX

JSX (JavaScript XML) is a syntax extension for JavaScript that allows us to write HTML-like code within JavaScript. JSX makes it easier to write and read React components.

Example:

```jsx
const element = <h1>Hello, world!</h1>;
```


## 3. Props

Props (short for properties) are a way of passing data from parent components to child components in React. Props are read-only and help make components reusable and modular.

Example:

```jsx
// Parent Component
const ParentComponent = () => {
  const greeting = "Hello, ";
  return <ChildComponent name="Ankit" greeting={greeting} />;
};

// Child Component
const ChildComponent = (props) => {
  return <p>{props.greeting}{props.name}</p>;
};
```

In this example, the `ParentComponent` passes the `name` and `greeting` props to the `ChildComponent`, which then displays the message "Hello, Ankit".

## 4. Composition and Fragments

Composition is the practice of combining multiple React components together to create more complex UI elements. Fragments allow us to group multiple children elements without adding extra nodes to the DOM.

Example:

```jsx
const App = () => {
  return (
    <>
      <Header />
      <MainContent />
      <Footer />
    </>
  );
};
```

In this example, `<>...</>` is a shorthand for `<React.Fragment>...</React.Fragment>`, which allows us to group `Header`, `MainContent`, and `Footer` components without introducing additional div elements.

## 5. Keys

Keys are special attributes that help React identify which items have changed, are added, or are removed in a list of elements. Keys should be unique among siblings.

Example:

```jsx
const listItems = numbers.map((number) => (
  <li key={number.toString()}>{number}</li>
));
```

In this example, each `li` element in the list is assigned a unique `key` attribute based on the `number` value to optimize rendering performance and maintain component state.

## 6. Rendering and Virtual DOM

Rendering is the process of converting React components into a DOM (Document Object Model) tree and displaying them in the browser. The Virtual DOM is a lightweight copy of the actual DOM maintained by React to improve performance.


## 7. Event Handling

Event handling in React allows us to respond to user interactions such as clicks, input changes, or form submissions. React provides built-in event handlers like `onClick`, `onChange`, and `onSubmit` to handle these events.

Example:

```jsx
const handleClick = () => {
  alert('Button clicked!');
};

return <button onClick={handleClick}>Click Me</button>;
```

In this example, the `handleClick` function is called when the button is clicked, triggering an alert message.

## 8. State and useState Hook

State in React represents the data that can change over time within a component. The `useState` hook is a function that allows functional components to use state.

Example:

```jsx
const [count, setCount] = useState(0);

const increment = () => {
  setCount(count + 1);
};

return (
  <div>
    <p>Count: {count}</p>
    <button onClick={increment}>Increment</button>
  </div>
);
```

In this example, the component maintains a `count` state variable initialized to 0, and the `increment` function updates the count when the button is clicked.

## 9. Controlled Components

Controlled components are React components whose form elements (like inputs) are controlled by React state. This means React handles the value and updates to the input fields.

Example:

```jsx
const [value, setValue] = useState('');

const handleChange = (event) => {
  setValue(event.target.value);
};

return (
  <input 
    type="text" 
    value={value} 
    onChange={handleChange} 
    placeholder="Type something" 
  />
);
```

In this example, the input field value is controlled by the `value` state variable, and changes to the input are handled by the `handleChange` function, updating the state accordingly.


## 10. React Hooks

React hooks are functions that enable functional components to use state and other React features without writing a class. There are several built-in hooks like `useState`, `useEffect`, `useContext`, etc., each serving a specific purpose.

Example:

```jsx
import React, { useState, useEffect } from 'react';

const MyComponent = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
};
```

In this example, the `useState` hook is used to manage state (`count`), and the `useEffect` hook is used to perform side effects (updating the document title) based on state changes.

## 11. Pure Components and Strict Mode

Pure components in React are components that always render the same output for the same input props. They optimize performance by avoiding unnecessary re-renders. Strict mode is a development mode that highlights potential problems in your app and ensures that your components are pure.

Example:

```jsx
import React, { PureComponent } from 'react';

class MyComponent extends PureComponent {
  render() {
    return <div>{this.props.value}</div>;
  }
}
```

In this example, `MyComponent` is a pure component because it extends `PureComponent` instead of `Component`, ensuring that it only re-renders when its props change.

## 12. Effects and useEffect Hook

Effects in React allow you to perform side effects in function components. They run after every completed render and can perform data fetching, subscriptions, or manually changing the DOM.

Example:

```jsx
import React, { useState, useEffect } from 'react';

const MyComponent = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
};
```

In this example, the `useEffect` hook is used to update the document title whenever the `count` state changes.

## 13. Refs and useRef Hook

Refs in React provide a way to access the DOM nodes or React elements created in the render method. They are commonly used to interact with child components, focus input fields, or trigger imperative animations.

Example:

```jsx
import React, { useRef } from 'react';

const MyComponent = () => {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
};
```

In this example, the `useRef` hook is used to create a ref that points to the input element. The `focusInput` function focuses on the input element when the button is clicked.

## 14. Context

Context in React provides a way to pass data through the component tree without having to pass props down manually at every level. It's useful for sharing common data, like themes or user preferences, across many components.

Example:

```jsx
import React, { createContext, useContext } from 'react';

const ThemeContext = createContext('light');

const ThemedButton = () => {
  const theme = useContext(ThemeContext);
  return <button style={{ background: theme }}>Click me</button>;
};

const App = () => {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedButton />
    </ThemeContext.Provider>
  );
};
```

In this example, the `ThemeContext.Provider` component provides the `ThemeContext` to the `ThemedButton` component, allowing it to access the current theme value.

## 15. Portals

Portals in React provide a way to render children into a DOM node that exists outside of the parent component's DOM hierarchy. They are useful for scenarios like modals, tooltips, or popovers that need to escape the parent's styling constraints.

Example:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

const Modal = ({ children }) => {
  return ReactDOM.createPortal(
    children,
    document.getElementById('modal-root')
  );
};

const App = () => {
  return (
    <div>
      <h1>Hello, world!</h1>
      <Modal>
        <p>This is a modal dialog</p>
      </Modal>
    </div>
  );
};
```

In this example, the `Modal` component renders its children into a DOM node with the ID `'modal-root'`, which exists outside the main DOM hierarchy of the `App` component.

## 16. Suspense

Suspense is a feature in React that allows components to wait for something to happen before rendering. It's particularly useful for handling asynchronous operations such as data fetching or code splitting.

Example:

```jsx
import React, { Suspense } from 'react';

const LazyComponent = React.lazy(() => import('./LazyComponent'));

const App = () => {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <LazyComponent />
      </Suspense>
    </div>
  );
};
```

In this example, the `Suspense` component wraps the lazy-loaded `LazyComponent`, providing a fallback UI to display while the component is being loaded.

## 17. Error Boundaries

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree and display a fallback UI instead of crashing the entire application. They are useful for handling errors gracefully and providing a better user experience.

Example:

```jsx
import React, { Component } from 'react';

class ErrorBoundary extends Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  componentDidCatch(error, errorInfo) {
    this.setState({ hasError: true });
    // Log error details to a monitoring service
    console.error(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <div>Something went wrong...</div>;
    }
    return this.props.children;
  }
}

export default ErrorBoundary;
```

In this example, the `ErrorBoundary` component catches errors thrown by its children and renders a fallback UI if an error occurs.


# Week 15 Learning Objectives

## Class Components

- Recognize a React Class Component

A Class Component is a component that is defined using JavaScript Class syntax and extends the React.Component class from the react package.
To render elements in a Class Component, you must define a render method on the class. The return value of the render method is what will be rendered by the component.

```js
import React from 'react';

class ClassComponent extends React.Component {
  constructor(props) {
    super(props); // must be called if creating a constructor method
  }

  render() {
    return <div></div>;
  }
}
```

- Convert the use of component props in a Class Component to a Function - Component

```js
import React from 'react';

class MyComponent extends React.Component {
  render() {
    return (
      <>
        <h1>{this.props.title}</h1>
      </>
    );
  }
}
```

becomes

```js
function MyComponent(props) {
  return (
    <>
      <h1>{props.title}</h1>
    </>
  );
}
```

- Convert the use of component state in a Class Component to a Function - Component using useState

```js
class ClassComponent extends React.Component {
  constructor(props) {
    super(props); // must be called if creating a constructor method

    // Initialize the component state object
    this.state = {
      count: 0
    };
  }

  render() {
    return (
      <>
        <h1>{this.props.title}</h1>
        <div>{count}</div>
        <button
          onClick={() => this.setState((state) => ({ count: state.count + 1 }))}
        >
          Increment
        </button>
      </>
    );
  }
}
```

becomes

```js
import { useState } from 'react';

function FunctionComponent({ title }) {
  const [count, setCount] = useState(0);

  return (
    <>
      <h1>{title}</h1>
      <div>{count}</div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </>
  );
}
```

- Understand what lifecycle methods are, the types of lifecycle methods, and when they are called when a Class Component is rendered

Lifecycle methods of a Class Component are methods that will be invoked after the rendering of a component. There are three types of lifecycle methods. componentDidMount will only run once, after the component's first render. componentDidUpdate will run after every render that isn't the first render. componentWillUnmount will run right before the component is removed from the component tree.

- Convert the use of lifecycle methods in a Class Component to a Function

```js
import React from 'react';

class ClassComponent extends React.Component {
  constructor(props) {
    super(props); // must be called if creating a constructor method

    // Initialize the component state object
    this.state = {
      count: 0
    };
  }

  componentDidMount() {
    setTimeout(() => {
      this.setState({ count: 0 });
    }, 1000);
  }

  componentDidUpdate(prevProps, prevState) {
    if (prevState.count !== this.state.count) {
      console.log('hello world!');
    }
  }

  componentWillUnmount() {
    console.log('cleanup');
  }

  render() {
    return (
      <>
        <div>{count}</div>
        <button
          onClick={() => this.setState((state) => ({ count: state.count + 1 }))}
        >
          Increment
        </button>
      </>
    );
  }
}
```

## React With Redux Objectives

- Describe the Redux data cycle.
- Evaluate when it's appropriate to use Redux.

For projects with more sophisticated global state requirements, Redux remains a popular option. Redux offers greater flexibility with support for middleware and richer developer tools in the form of the Redux DevTools.

- Configure a React application to use Redux.

- Configure Redux to use the browser extension for Redux development tools.
- Change the Redux store state using reducers and actions.
- Use composed reducers to organize state management into smaller pieces.
- Configure a React component to subscribe to changes in the Redux store.
- Change Redux state in components using hooks.
- Define a 'slice of state'.
- Debug Redux by using browser window object.
- Use debugging tools to determine when an action is called and a reducer updates state.
- Create a Redux store with preloaded state.
- Describe why reducers return a new reference in memory to update the state.
- Compare and contrast an action and an action creator.
- Use constants to define action types to prevent simple typos.
- Explain why all actions hit all reducers.

# Redux with Thunk and Fetching

- Attach middleware to the Redux store.
- Debug using the Redux Logger.
- Evaluate when it is appropriate to use Thunk.
- Define a fetch request to an API.
- Write a thunk action creator to make an asynchronous request to an API and dispatch another action when the response is received.
- Refactor an async call in a React component to use Redux with Thunk.

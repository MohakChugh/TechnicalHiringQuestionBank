# React.js Developer Interview Questions

## Core React Concepts

### 1. What is React and what are its key features?
**Answer:** React is a JavaScript library for building user interfaces, particularly single-page applications. Its key features include:

- **Virtual DOM:** React creates an in-memory data structure, compares it with the real DOM, and updates only what has changed, improving performance.
- **Component-Based Architecture:** UI is broken down into reusable, self-contained components.
- **Unidirectional Data Flow:** Data flows one way from parent to child components, making the application more predictable and easier to debug.
- **JSX:** A syntax extension that allows writing HTML-like code in JavaScript.
- **React Native:** Ability to build mobile applications using the same component concepts.
- **Declarative Approach:** You describe what you want the UI to look like based on the current state, and React handles the DOM updates.
- **Rich Ecosystem:** Extensive libraries, tools, and community support.

### 2. Explain the difference between functional and class components.
**Answer:**

**Class Components:**
```jsx
class Welcome extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  handleClick = () => {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <h1>Hello, {this.props.name}</h1>
        <p>Count: {this.state.count}</p>
        <button onClick={this.handleClick}>Increment</button>
      </div>
    );
  }
}
```

**Functional Components (with Hooks):**
```jsx
function Welcome(props) {
  const [count, setCount] = React.useState(0);

  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h1>Hello, {props.name}</h1>
      <p>Count: {count}</p>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
}
```

**Key Differences:**
- **Syntax:** Class components use ES6 classes and extend from React.Component, while functional components are JavaScript functions.
- **State Management:** Class components use this.state and this.setState(), while functional components use the useState hook.
- **Lifecycle Methods:** Class components have lifecycle methods (componentDidMount, etc.), while functional components use the useEffect hook.
- **'this' Keyword:** Class components require 'this' to access props, state, and methods, while functional components don't use 'this'.
- **Performance:** Functional components can have slightly better performance and smaller bundle size.
- **Modern Approach:** Functional components with hooks are the recommended approach in modern React development.

### 3. What are React Hooks and why were they introduced?
**Answer:** React Hooks are functions that let you "hook into" React state and lifecycle features from functional components. They were introduced in React 16.8 to:

- Allow using state and other React features without writing a class
- Make it easier to reuse stateful logic between components
- Organize related code better (by logical concern rather than lifecycle methods)
- Avoid the complexity of class components (this binding, understanding lifecycle methods)
- Enable more optimizations by the React compiler

**Common Built-in Hooks:**

1. **useState:** Adds state to functional components
```jsx
const [count, setCount] = useState(0);
```

2. **useEffect:** Handles side effects (similar to componentDidMount, componentDidUpdate, componentWillUnmount)
```jsx
useEffect(() => {
  document.title = `You clicked ${count} times`;

  return () => {
    // Cleanup code (componentWillUnmount equivalent)
  };
}, [count]); // Only re-run if count changes
```

3. **useContext:** Accesses context without nesting
```jsx
const theme = useContext(ThemeContext);
```

4. **useReducer:** Manages complex state logic
```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

5. **useCallback:** Returns a memoized callback function
```jsx
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
```

6. **useMemo:** Returns a memoized value
```jsx
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

7. **useRef:** Creates a mutable ref object
```jsx
const inputRef = useRef(null);
// Later: inputRef.current.focus();
```

### 4. Explain the concept of the Virtual DOM and how it works.
**Answer:** The Virtual DOM is a lightweight JavaScript representation of the actual DOM. React uses it to improve performance and provide a declarative API.

**How it works:**

1. **Initial Render:**
   - React creates a virtual DOM tree representing the UI
   - React renders the actual DOM based on this virtual tree

2. **When State Changes:**
   - A new virtual DOM tree is created representing the updated UI
   - React performs "diffing" (using the Reconciliation algorithm) to compare the new virtual DOM with the previous one
   - It identifies the minimal set of changes needed to update the actual DOM
   - Only those specific changes are applied to the real DOM

3. **Benefits:**
   - Batch updates to minimize DOM manipulation
   - Abstract browser-specific DOM implementation details
   - Enable declarative API (describe what the UI should look like, not how to change it)
   - Support for features like server-side rendering and React Native

**Example of the Process:**
```jsx
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

When the button is clicked:
1. State updates from `count = 0` to `count = 1`
2. React creates a new virtual DOM tree with the updated count
3. React compares this new tree with the previous one
4. React identifies that only the text content of the `<p>` element needs to change
5. React updates only that specific part of the actual DOM

### 5. What is JSX and why is it used in React?
**Answer:** JSX (JavaScript XML) is a syntax extension for JavaScript that looks similar to HTML or XML. It allows you to write HTML-like code in your JavaScript files.

**Example:**
```jsx
const element = <h1 className="greeting">Hello, world!</h1>;
```

**Behind the scenes, JSX is transformed to regular JavaScript:**
```javascript
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```

**Benefits of JSX:**
- **Familiarity:** Easier for developers who know HTML
- **Visual clarity:** More intuitive to see the UI structure compared to nested function calls
- **Syntactic sugar:** Makes component rendering code more readable
- **Type safety:** Can use TypeScript with JSX for type checking
- **Compile-time optimizations:** Errors can be caught during compilation
- **Co-location:** Keeps rendering logic and UI markup together

**JSX Features:**
- Can embed JavaScript expressions using curly braces: `{expression}`
- Uses camelCase property naming (e.g., `className` instead of `class`)
- Self-closing tags for elements without children: `<img src="..." />`
- Can contain children elements
- Prevents injection attacks by escaping embedded values

### 6. Explain state and props in React.
**Answer:**

**Props (Properties):**
- Passed from parent to child components
- Read-only and immutable within the component
- Used to customize components or pass data down the component tree
- Changes in props trigger re-renders

```jsx
// Parent component
function ParentComponent() {
  return <ChildComponent name="John" age={30} />;
}

// Child component
function ChildComponent(props) {
  return (
    <div>
      <p>Name: {props.name}</p>
      <p>Age: {props.age}</p>
    </div>
  );
}
```

**State:**
- Managed within a component
- Mutable and can be updated using setState (class components) or state updater functions (hooks)
- Changes in state trigger re-renders
- Should contain minimal data needed for rendering

```jsx
// Using state in a functional component
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

// Using state in a class component
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}
```

**Key Differences:**
- Props are passed from parent to child; state is managed within the component
- Props are immutable; state can be updated
- Props are used for communication between components; state is for internal component data
- Changes in either props or state trigger a re-render

### 7. What is the significance of keys in React lists?
**Answer:** Keys are special attributes that help React identify which items in a list have changed, been added, or removed. They help React optimize the rendering of lists by providing a stable identity for each element.

**Purpose of Keys:**
- Enable efficient updates by identifying which elements have changed
- Help maintain component state across re-renders
- Prevent unnecessary re-renders of unchanged components
- Essential for React's reconciliation algorithm

**Example:**
```jsx
function TodoList({ todos }) {
  return (
    <ul>
      {todos.map(todo => (
        <li key={todo.id}>{todo.text}</li>
      ))}
    </ul>
  );
}
```

**Rules for Keys:**
- Keys must be unique among siblings (not globally)
- Keys should be stable, predictable, and unique
- Use IDs from your data when available
- Avoid using array indices as keys when the list can reorder (can cause performance issues and bugs with component state)
- Keys are not passed to components as props (need to pass explicitly if needed)

**What happens without keys:**
Without keys, React has to re-render the entire list when something changes, which can lead to performance issues and potential bugs with component state.

### 8. Explain the useEffect hook and its common use cases.
**Answer:** The useEffect hook lets you perform side effects in functional components. It serves similar purposes to componentDidMount, componentDidUpdate, and componentWillUnmount in class components.

**Basic Syntax:**
```jsx
useEffect(() => {
  // Side effect code

  return () => {
    // Cleanup code (optional)
  };
}, [dependencies]); // Dependencies array (optional)
```

**Behavior Based on Dependencies:**
- **No dependency array:** Effect runs after every render
- **Empty dependency array (`[]`):** Effect runs only once after the initial render
- **With dependencies:** Effect runs after initial render and when any dependency changes

**Common Use Cases:**

1. **Data Fetching:**
```jsx
useEffect(() => {
  const fetchData = async () => {
    setLoading(true);
    try {
      const response = await fetch('https://api.example.com/data');
      const data = await response.json();
      setData(data);
    } catch (error) {
      setError(error);
    } finally {
      setLoading(false);
    }
  };

  fetchData();
}, []);
```

2. **Subscriptions/Event Listeners:**
```jsx
useEffect(() => {
  window.addEventListener('resize', handleResize);

  return () => {
    window.removeEventListener('resize', handleResize);
  };
}, []);
```

3. **DOM Manipulations:**
```jsx
useEffect(() => {
  const element = document.getElementById('my-element');
  element.classList.add('visible');

  return () => {
    element.classList.remove('visible');
  };
}, []);
```

4. **Timers:**
```jsx
useEffect(() => {
  const timer = setTimeout(() => {
    setShowNotification(false);
  }, 3000);

  return () => {
    clearTimeout(timer);
  };
}, []);
```

5. **Synchronizing with Props/State:**
```jsx
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]);
```

6. **Logging/Analytics:**
```jsx
useEffect(() => {
  logPageView(page);
}, [page]);
```

### 9. What is the Context API and when would you use it?
**Answer:** The Context API provides a way to share values like themes, user data, or language preferences between components without explicitly passing props through every level of the component tree.

**When to Use Context:**
- For global data needed by many components at different nesting levels
- When passing props through many intermediate components becomes cumbersome (prop drilling)
- For data that can be considered "global" for a tree of components
- For theme implementation, user authentication state, language preferences, etc.

**Basic Usage:**

1. **Create a Context:**
```jsx
// ThemeContext.js
import { createContext } from 'react';

export const ThemeContext = createContext('light');
```

2. **Provide Context Value:**
```jsx
// App.js
import { ThemeContext } from './ThemeContext';

function App() {
  const [theme, setTheme] = useState('light');

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <MainContent />
    </ThemeContext.Provider>
  );
}
```

3. **Consume Context Value:**

Using useContext hook (functional components):
```jsx
import { useContext } from 'react';
import { ThemeContext } from './ThemeContext';

function ThemedButton() {
  const { theme, setTheme } = useContext(ThemeContext);

  return (
    <button
      className={theme === 'dark' ? 'dark-button' : 'light-button'}
      onClick={() => setTheme(theme === 'dark' ? 'light' : 'dark')}
    >
      Toggle Theme
    </button>
  );
}
```

Using Consumer component (works in any component):
```jsx
import { ThemeContext } from './ThemeContext';

function ThemedButton() {
  return (
    <ThemeContext.Consumer>
      {({ theme, setTheme }) => (
        <button
          className={theme === 'dark' ? 'dark-button' : 'light-button'}
          onClick={() => setTheme(theme === 'dark' ? 'light' : 'dark')}
        >
          Toggle Theme
        </button>
      )}
    </ThemeContext.Consumer>
  );
}
```

**Best Practices:**
- Don't overuse Context for data that should be passed as props
- Consider splitting contexts by domain (ThemeContext, UserContext, etc.)
- For complex state management, consider combining Context with useReducer
- Be mindful of re-renders when context values change

### 10. What are controlled and uncontrolled components?
**Answer:**

**Controlled Components:**
Components where form data is handled by React state. The React component controls the input's value at all times.

```jsx
function ControlledForm() {
  const [name, setName] = useState('');

  const handleChange = (event) => {
    setName(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert('A name was submitted: ' + name);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={handleChange} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}
```

**Characteristics of Controlled Components:**
- Form data is handled by React state
- Current value is passed as a prop
- Changes are handled through callbacks (like onChange)
- More control over form validation and submission
- More predictable as React is the "single source of truth"

**Uncontrolled Components:**
Components where form data is handled by the DOM itself. Values are retrieved using refs when needed.

```jsx
function UncontrolledForm() {
  const inputRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    alert('A name was submitted: ' + inputRef.current.value);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" defaultValue="Default name" ref={inputRef} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}
```

**Characteristics of Uncontrolled Components:**
- Form data is handled by the DOM
- Initial values set with defaultValue attribute
- Values accessed using refs
- Less code for simple forms
- Useful when integrating with non-React code

**When to Use Each:**
- **Controlled Components:** When you need immediate validation, conditional disabling of submit button, enforcing input format, or dynamic inputs
- **Uncontrolled Components:** For simple forms, when integrating with non-React code, or for performance optimization in rare cases

## Advanced React Concepts

### 11. What is Redux and when would you use it?
**Answer:** Redux is a predictable state container for JavaScript applications, commonly used with React for managing application state.

**Core Concepts:**
- **Single Source of Truth:** The entire application state is stored in a single store
- **State is Read-Only:** State can only be changed by dispatching actions
- **Changes are Made with Pure Functions:** Reducers are pure functions that take the previous state and an action to return the new state

**When to Use Redux:**
- When multiple components need to access and update the same state
- When the app state becomes complex and needs to be managed in a predictable way
- When you need to persist state across page refreshes or share state across routes
- When you need time-travel debugging or other advanced debugging capabilities
- When you need middleware for async operations or logging

**Basic Redux Flow:**
1. Component dispatches an action
2. The action is processed by a reducer
3. The reducer updates the store
4. The store notifies subscribed components
5. Components re-render with the new state

**Example with React-Redux:**
```jsx
// Action Types
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

// Action Creators
const increment = () => ({ type: INCREMENT });
const decrement = () => ({ type: DECREMENT });

// Reducer
const counterReducer = (state = { count: 0 }, action) => {
  switch (action.type) {
    case INCREMENT:
      return { count: state.count + 1 };
    case DECREMENT:
      return { count: state.count - 1 };
    default:
      return state;
  }
};

// Store
import { createStore } from 'redux';
const store = createStore(counterReducer);

// Component
import { useSelector, useDispatch } from 'react-redux';

function Counter() {
  const count = useSelector(state => state.count);
  const dispatch = useDispatch();

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
    </div>
  );
}

// Provider
import { Provider } from 'react-redux';

function App() {
  return (
    <Provider store={store}>
      <Counter />
    </Provider>
  );
}
```

**Alternatives to Consider:**
- Context API + useReducer for simpler applications
- Zustand, Recoil, Jotai, or MobX for different state management approaches
- React Query or SWR for server state management

### 12. Explain React's component lifecycle methods and their hooks equivalents.
**Answer:**

**Class Component Lifecycle Methods:**

**Mounting Phase:**
- `constructor()` - Initialize state and bind methods
- `static getDerivedStateFromProps()` - Update state based on props
- `render()` - Render the component
- `componentDidMount()` - Run after component is mounted (DOM is ready)

**Updating Phase:**
- `static getDerivedStateFromProps()` - Update state based on changed props
- `shouldComponentUpdate()` - Control if component should re-render
- `render()` - Re-render with new props/state
- `getSnapshotBeforeUpdate()` - Capture information before DOM updates
- `componentDidUpdate()` - Run after component updates

**Unmounting Phase:**
- `componentWillUnmount()` - Clean up before component is removed

**Error Handling:**
- `static getDerivedStateFromError()` - Update state after error
- `componentDidCatch()` - Handle errors

**Hooks Equivalents:**

| Class Lifecycle Method | Hooks Equivalent |
|------------------------|------------------|
| `constructor()` | `useState()` |
| `componentDidMount()` | `useEffect(() => {}, [])` |
| `componentDidUpdate()` | `useEffect(() => {}, [dependencies])` |
| `componentWillUnmount()` | `useEffect(() => { return () => {} }, [])` |
| `shouldComponentUpdate()` | `React.memo()`, `useMemo()`, `useCallback()` |
| `getDerivedStateFromProps()` | `useEffect()` that updates state based on prop changes |
| Error boundaries | No direct equivalent yet (still use class components) |

**Example Comparison:**

**Class Component:**
```jsx
class Timer extends React.Component {
  constructor(props) {
    super(props);
    this.state = { seconds: 0 };
  }

  componentDidMount() {
    this.interval = setInterval(() => {
      this.setState(state => ({ seconds: state.seconds + 1 }));
    }, 1000);
  }

  componentDidUpdate(prevProps) {
    if (this.props.reset !== prevProps.reset) {
      this.setState({ seconds: 0 });
    }
  }

  componentWillUnmount() {
    clearInterval(this.interval);
  }

  render() {
    return <div>Seconds: {this.state.seconds}</div>;
  }
}
```

**Functional Component with Hooks:**
```jsx
function Timer(props) {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds(seconds => seconds + 1);
    }, 1000);

    return () => clearInterval(interval);
  }, []);

  useEffect(() => {
    setSeconds(0);
  }, [props.reset]);

  return <div>Seconds: {seconds}</div>;
}
```

### 13. What are React render props and higher-order components (HOCs)?
**Answer:** Both render props and higher-order components (HOCs) are patterns for code reuse and component composition in React.

**Render Props:**
A technique where a component receives a function prop that returns a React element, allowing the component to call this function instead of implementing its own rendering logic.

```jsx
// MouseTracker component using render props
class MouseTracker extends React.Component {
  state = { x: 0, y: 0 };

  handleMouseMove = (event) => {
    this.setState({
      x: event.clientX,
      y: event.clientY
    });
  };

  render() {
    return (
      <div style={{ height: '100vh' }} onMouseMove={this.handleMouseMove}>
        {this.props.render(this.state)}
      </div>
    );
  }
}

// Usage
<MouseTracker
  render={({ x, y }) => (
    <h1>The mouse position is ({x}, {y})</h1>
  )}
/>
```

**Higher-Order Components (HOCs):**
A function that takes a component and returns a new enhanced component with additional props or behavior.

```jsx
// withMousePosition HOC
function withMousePosition(WrappedComponent) {
  return class extends React.Component {
    state = { x: 0, y: 0 };

    handleMouseMove = (event) => {
      this.setState({
        x: event.clientX,
        y: event.clientY
      });
    };

    render() {
      return (
        <div style={{ height: '100vh' }} onMouseMove={this.handleMouseMove}>
          <WrappedComponent {...this.props} mousePosition={this.state} />
        </div>
      );
    }
  };
}

// Usage
const MouseDisplay = ({ mousePosition }) => (
  <h1>The mouse position is ({mousePosition.x}, {mousePosition.y})</h1>
);

const EnhancedMouseDisplay = withMousePosition(MouseDisplay);

// In your app
<EnhancedMouseDisplay />
```

**Comparison:**

| Aspect | Render Props | HOCs |
|--------|--------------|------|
| Implementation | Uses a function prop | Uses a function that returns a component |
| Composition | Explicit at render time | Implicit at component definition |
| Props Collision | No collision issues | Potential naming conflicts |
| Debugging | Clearer component hierarchy | Wrapped components can be harder to debug |
| Modern Alternative | Custom hooks often replace both patterns | Custom hooks often replace both patterns |

**Modern Alternative - Custom Hooks:**
```jsx
// useMousePosition hook
function useMousePosition() {
  const [position, setPosition] = useState({ x: 0, y: 0 });

  useEffect(() => {
    const handleMouseMove = (event) => {
      setPosition({ x: event.clientX, y: event.clientY });
    };

    window.addEventListener('mousemove', handleMouseMove);

    return () => {
      window.removeEventListener('mousemove', handleMouseMove);
    };
  }, []);

  return position;
}

// Usage
function MouseDisplay() {
  const { x, y } = useMousePosition();
  return <h1>The mouse position is ({x}, {y})</h1>;
}
```

### 14. How do you optimize performance in React applications?
**Answer:** React applications can be optimized through various techniques:

**1. Component Optimization:**
- **React.memo:** Memoize functional components to prevent unnecessary re-renders
  ```jsx
  const MemoizedComponent = React.memo(function MyComponent(props) {
    // Only re-renders if props change
    return <div>{props.name}</div>;
  });
  ```

- **PureComponent/shouldComponentUpdate:** For class components
  ```jsx
  class OptimizedComponent extends React.PureComponent {
    // Only re-renders if props or state change (shallow comparison)
    render() {
      return <div>{this.props.name}</div>;
    }
  }
  ```

**2. Hooks Optimization:**
- **useMemo:** Memoize expensive calculations
  ```jsx
  const memoizedValue = useMemo(() => {
    return computeExpensiveValue(a, b);
  }, [a, b]);
  ```

- **useCallback:** Memoize callback functions
  ```jsx
  const memoizedCallback = useCallback(() => {
    doSomething(a, b);
  }, [a, b]);
  ```

**3. List Optimization:**
- **Virtualization:** Render only visible items in long lists
  ```jsx
  import { FixedSizeList } from 'react-window';

  function VirtualizedList({ items }) {
    const Row = ({ index, style }) => (
      <div style={style}>{items[index]}</div>
    );

    return (
      <FixedSizeList
        height={500}
        width={300}
        itemCount={items.length}
        itemSize={35}
      >
        {Row}
      </FixedSizeList>
    );
  }
  ```

**4. Code Splitting:**
- **React.lazy and Suspense:** Load components only when needed
  ```jsx
  const LazyComponent = React.lazy(() => import('./LazyComponent'));

  function MyComponent() {
    return (
      <React.Suspense fallback={<div>Loading...</div>}>
        <LazyComponent />
      </React.Suspense>
    );
  }
  ```

**5. State Management Optimization:**
- Keep state as local as possible
- Use appropriate state management tools (Context, Redux, etc.)
- Normalize complex state structures

**6. Rendering Optimization:**
- Avoid inline function definitions in render
- Use keys correctly in lists
- Avoid unnecessary re-renders with proper dependency arrays in useEffect

**7. Bundle Optimization:**
- Code splitting with dynamic imports
- Tree shaking to eliminate dead code
- Minification and compression
- Use production builds

**8. Network Optimization:**
- Implement proper data fetching strategies
- Use caching mechanisms
- Consider server-side rendering or static generation

**9. Profiling and Monitoring:**
- Use React DevTools Profiler
- Implement performance monitoring
- Set performance budgets

**10. Image and Asset Optimization:**
- Lazy load images
- Use appropriate image formats and sizes
- Optimize assets

### 15. What are React Fragments and why are they useful?
**Answer:** React Fragments are a feature that allows you to group multiple elements without adding an extra node to the DOM.

**Syntax:**
```jsx
// Long syntax (with key support)
<React.Fragment key="unique-key">
  <ChildA />
  <ChildB />
  <ChildC />
</React.Fragment>

// Short syntax (no key support)
<>
  <ChildA />
  <ChildB />
  <ChildC />
</>
```

**Benefits:**
1. **Cleaner DOM:** No additional wrapper div or span elements in the rendered HTML
2. **Valid JSX:** Satisfies the requirement that components must return a single root element
3. **Better Performance:** Slightly better performance by avoiding unnecessary DOM nodes
4. **CSS Flexibility:** Avoids breaking CSS flexbox and grid layouts
5. **Table Integrity:** Allows proper rendering of `<tr>` elements inside `<tbody>` without extra elements

**Example Use Case:**
```jsx
// Without Fragments (adds extra div)
function Table() {
  return (
    <table>
      <tbody>
        <tr>
          <Columns />
        </tr>
      </tbody>
    </table>
  );
}

function Columns() {
  return (
    <div>
      <td>Column 1</td>
      <td>Column 2</td>
    </div>
  ); // This breaks table structure!
}

// With Fragments (maintains table structure)
function Columns() {
  return (
    <>
      <td>Column 1</td>
      <td>Column 2</td>
    </>
  );
}
```

**When to Use Fragments:**
- When returning multiple elements from a component
- When adding elements to a list without a wrapper
- When working with table rows and columns
- When you want to avoid unnecessary DOM nesting
- When CSS selectors or flexbox/grid would be affected by extra divs
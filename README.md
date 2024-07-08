# Most Asked Questions for ReactJS

1. **What is React?**
   - **Answer**: React is a JavaScript library for building user interfaces. It allows you to create reusable UI components and efficiently update and render components when data changes.
   - **Example**:
     ```jsx
     function Welcome() {
       return <h1>Hello, World!</h1>;
     }
     ```

2. **What is `useMemo`?**
   - **Answer**: `useMemo` is a React hook that memoizes the result of a computation, preventing expensive calculations on every render if the dependencies haven't changed.
   - **Example**:
     ```jsx
     const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
     ```

3. **What are the features of React?**
   - **Answer**: React's features include JSX, Virtual DOM, component-based architecture, unidirectional data flow, and hooks for managing state and side effects.
   - **Example**:
     ```jsx
     const element = <h1>Hello, world!</h1>; // JSX
     ```

4. **What is JSX?**
   - **Answer**: JSX is a syntax extension for JavaScript that resembles HTML and is used with React to describe the UI. It makes writing React components easier and more readable.
   - **Example**:
     ```jsx
     const element = <h1>Hello, world!</h1>;
     ```

5. **What is DOM?**
   - **Answer**: The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content.
   - **Example**:
     ```html
     <div id="root"></div>
     ```

6. **What is Virtual DOM?**
   - **Answer**: The Virtual DOM is a lightweight, in-memory representation of the actual DOM. React uses it to efficiently update the real DOM by minimizing re-renders.
   - **Example**:
     ```jsx
     const element = <h1>Hello, world!</h1>; // React updates Virtual DOM first
     ```

7. **What is the component life cycle of a React class component?**
   - **Answer**: React class components have lifecycle methods such as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`, which allow you to run code at specific times in a component's life.
   - **Example**:
     ```jsx
     class MyComponent extends React.Component {
       componentDidMount() {
         // Runs after the component is mounted
       }
       render() {
         return <div>Hello, world!</div>;
       }
     }
     ```

8. **What are fragments in React?**
   - **Answer**: Fragments let you group multiple elements without adding extra nodes to the DOM. They help in returning multiple elements from a component's render method.
   - **Example**:
     ```jsx
     return (
       <React.Fragment>
         <h1>Hello</h1>
         <h2>World</h2>
       </React.Fragment>
     );
     ```

9. **What are props in React?**
   - **Answer**: Props are inputs to a React component that allow data to be passed from parent to child components. They are read-only and help in component communication.
   - **Example**:
     ```jsx
     function Welcome(props) {
       return <h1>Hello, {props.name}</h1>;
     }
     ```

10. **What are synthetic events in React?**
    - **Answer**: Synthetic events are React's cross-browser wrapper around the browser's native events. They provide a consistent API for handling events across different browsers.
    - **Example**:
      ```jsx
      function handleClick(event) {
        console.log(event);
      }
      ```

11. **What are the differences between `package.json` and `package-lock.json`?**
    - **Answer**: `package.json` lists project dependencies, while `package-lock.json` locks the specific versions of dependencies, ensuring consistent installs.
    - **Example**:
      ```json
      // package.json
      "dependencies": {
        "react": "^17.0.2"
      }

      // package-lock.json
      "react": {
        "version": "17.0.2",
        "resolved": "https://registry.npmjs.org/react/-/react-17.0.2.tgz",
        "integrity": "sha512-..."
      }
      ```

12. **What are the differences between client-side and server-side rendering?**
    - **Answer**: Client-side rendering renders content in the browser using JavaScript, while server-side rendering renders content on the server and sends it to the client.
    - **Example**:
      ```jsx
      // Client-side
      ReactDOM.render(<App />, document.getElementById('root'));

      // Server-side
      const html = ReactDOMServer.renderToString(<App />);
      ```

13. **What is state in ReactJS?**
    - **Answer**: State is an object that holds data that may change over the lifetime of a component. It enables dynamic and interactive components.
    - **Example**:
      ```jsx
      class MyComponent extends React.Component {
        constructor(props) {
          super(props);
          this.state = { count: 0 };
        }
      }
      ```

14. **What are props?**
    - **Answer**: Props are inputs to React components that allow data to be passed from a parent component to a child component. They are read-only and help in component communication.
    - **Example**:
      ```jsx
      function Welcome(props) {
        return <h1>Hello, {props.name}</h1>;
      }
      ```

15. **What are the differences between state and props in React?**
    - **Answer**: State is local to the component and can change over time, while props are passed from parent to child components and are read-only.
    - **Example**:
      ```jsx
      class MyComponent extends React.Component {
        constructor(props) {
          super(props);
          this.state = { count: 0 }; // state
        }
        render() {
          return <ChildComponent name={this.props.name} />; // props
        }
      }
      ```

16. **What is props drilling?**
    - **Answer**: Props drilling is the process of passing props through multiple levels of components to reach a deeply nested component.
    - **Example**:
      ```jsx
      <ParentComponent>
        <ChildComponent>
          <GrandChildComponent name={name} />
        </ChildComponent>
      </ParentComponent>
      ```

17. **What are the disadvantages of props drilling and how can we avoid it?**
    - **Answer**: Props drilling makes code harder to maintain by passing props through many layers. It can be avoided using Context API or state management libraries like Redux.
    - **Example**:
      ```jsx
      const MyContext = React.createContext();
      ```

18. **What are pure components in React?**
    - **Answer**: Pure components perform a shallow comparison of props and state to decide if a re-render is necessary, improving performance by preventing unnecessary renders.
    - **Example**:
      ```jsx
      class MyComponent extends React.PureComponent {
        render() {
          return <div>{this.props.value}</div>;
        }
      }
      ```

19. **What are refs in React?**
    - **Answer**: Refs provide a way to access DOM nodes or React elements directly, allowing for manipulation or interaction with the DOM.
    - **Example**:
      ```jsx
      const inputRef = React.createRef();
      ```

20. **What is meant by forward ref?**
    - **Answer**: Forward ref is a technique for passing a ref through a component to one of its children, enabling parent components to interact with the child component's DOM nodes.
    - **Example**:
      ```jsx
      const FancyButton = React.forwardRef((props, ref) => (
        <button ref={ref}>{props.children}</button>
      ));
      ```

21. **What are error boundaries?**
    - **Answer**: Error boundaries are React components that catch JavaScript errors anywhere in their child component tree and display a fallback UI instead of crashing the whole app.
    - **Example**:
      ```jsx
      class ErrorBoundary extends React.Component {
        componentDidCatch(error, info) {
          // Handle error
        }
        render() {
          return this.props.children;
        }
      }
      ```

22. **What are higher-order components in React?**
    - **Answer**: Higher-order components (HOCs) are functions that take a component and return a new component, allowing for reusing component logic.
    - **Example**:
      ```jsx
      function withLogging(WrappedComponent) {
        return class extends React.Component {
          render() {
            return <WrappedComponent {...this.props} />;
          }
        };
      }
      ```

23. **What are the differences between controlled and uncontrolled components?**
    - **Answer**: Controlled components have their state controlled by React, while uncontrolled components store their state in the DOM.
    - **Example**:
      ```jsx
      // Controlled
      <input value={this.state.value} onChange={this.handleChange} />

      // Uncontrolled
      <input defaultValue="default" ref={this.inputRef} />
      ```

24. **What is `useCallback`?**
    - **Answer**: `useCallback` is a hook that returns

 a memoized version of a callback function, preventing unnecessary re-creations of the function on each render.
    - **Example**:
      ```jsx
      const memoizedCallback = useCallback(() => {
        doSomething(a, b);
      }, [a, b]);
      ```

25. **What are the differences between `useMemo` and `useCallback`?**
    - **Answer**: `useMemo` memoizes a value, while `useCallback` memoizes a function. Both optimize performance by avoiding unnecessary recalculations or re-creations.
    - **Example**:
      ```jsx
      const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
      const memoizedCallback = useCallback(() => doSomething(a, b), [a, b]);
      ```

26. **What are keys in React?**
    - **Answer**: Keys are unique identifiers for elements in an array, helping React identify which items have changed, are added, or are removed.
    - **Example**:
      ```jsx
      const listItems = items.map((item) => <li key={item.id}>{item.name}</li>);
      ```

27. **What is lazy loading in React?**
    - **Answer**: Lazy loading is a technique for loading components only when they are needed, improving the performance of your app.
    - **Example**:
      ```jsx
      const OtherComponent = React.lazy(() => import('./OtherComponent'));
      ```

28. **What is suspense in React?**
    - **Answer**: Suspense allows you to show a fallback component while waiting for some code or data to load, enhancing user experience during loading states.
    - **Example**:
      ```jsx
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
      ```

29. **What are custom hooks?**
    - **Answer**: Custom hooks are functions that let you use stateful logic and can be reused across components, promoting code reuse and organization.
    - **Example**:
      ```jsx
      function useCustomHook() {
        const [count, setCount] = useState(0);
        return [count, setCount];
      }
      ```

30. **What is `useReducer` hook?**
    - **Answer**: `useReducer` is a hook for managing complex state logic by using a reducer function, providing an alternative to `useState`.
    - **Example**:
      ```jsx
      const [state, dispatch] = useReducer(reducer, initialState);
      ```

31. **What are portals in React?**
    - **Answer**: Portals provide a way to render children into a DOM node outside the component's parent, useful for modals and overlays.
    - **Example**:
      ```jsx
      ReactDOM.createPortal(<Child />, document.getElementById('portal-root'));
      ```

32. **What is context in React?**
    - **Answer**: Context provides a way to pass data through the component tree without passing props down manually at every level, useful for global data like themes or user info.
    - **Example**:
      ```jsx
      const MyContext = React.createContext();
      ```

33. **Practical question: Give an example of context API usage.**
    - **Example**:
      ```jsx
      const MyContext = React.createContext();
      function MyProvider({ children }) {
        const [value, setValue] = useState('Hello');
        return <MyContext.Provider value={value}>{children}</MyContext.Provider>;
      }
      ```

34. **What is the purpose of a callback function as an argument of `setState()`?**
    - **Answer**: It ensures the state is updated before running some code, useful for executing code right after state changes.
    - **Example**:
      ```jsx
      this.setState({ count: this.state.count + 1 }, () => {
        console.log(this.state.count);
      });
      ```

35. **Practical question: Create a custom hook for an increment/decrement counter.**
    - **Example**:
      ```jsx
      function useCounter(initialValue = 0) {
        const [count, setCount] = useState(initialValue);
        const increment = () => setCount(count + 1);
        const decrement = () => setCount(count - 1);
        return { count, increment, decrement };
      }
      ```

36. **Which lifecycle hooks in class components are replaced with `useEffect` in functional components?**
    - **Answer**: `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` are replaced with `useEffect` in functional components.
    - **Example**:
      ```jsx
      useEffect(() => {
        // Code to run on mount and update
        return () => {
          // Code to run on unmount
        };
      }, []);
      ```

37. **What is strict mode in React?**
    - **Answer**: Strict Mode helps identify unsafe lifecycles, legacy API usage, and other potential issues, running checks and warnings in development mode.
    - **Example**:
      ```jsx
      <React.StrictMode>
        <App />
      </React.StrictMode>
      ```

38. **What are the different ways to pass data from child component to parent component in React?**
    - **Answer**: Using callback functions or `useRef`, allowing the child to send data or interact with the parent.
    - **Example**:
      ```jsx
      function Parent() {
        const handleData = (data) => {
          console.log(data);
        };
        return <Child onData={handleData} />;
      }
      ```

39. **Practical question: How to send data from child to parent using callback functions?**
    - **Example**:
      ```jsx
      function Child({ onData }) {
        return <button onClick={() => onData('Hello')}>Send Data</button>;
      }
      ```

40. **Practical question: How to send data from child component to parent using `useRef`?**
    - **Example**:
      ```jsx
      function Parent() {
        const childRef = useRef();
        return <Child ref={childRef} />;
      }

      const Child = forwardRef((props, ref) => {
        useImperativeHandle(ref, () => ({
          sendData() {
            return 'Hello';
          },
        }));
        return <div>Child</div>;
      });
      ```

41. **How do you optimize your React application?**
    - **Answer**: Use code splitting, memoization, lazy loading, and avoiding unnecessary re-renders to improve performance.
    - **Example**:
      ```jsx
      const MemoizedComponent = React.memo(Component);
      ```

42. **How would you consume a RESTful JSON API in ReactJS?**
    - **Answer**: Using `fetch` or `axios` to make HTTP requests, and handling the response data within your component.
    - **Example**:
      ```jsx
      useEffect(() => {
        fetch('https://api.example.com/data')
          .then(response => response.json())
          .then(data => setData(data));
      }, []);
      ```

43. **Different design patterns used in React?**
    - **Answer**: Common design patterns include component patterns, Higher-Order Components (HOCs), Render Props, Container/Presentational components, and Hooks.
    - **Example**:
      ```jsx
      const withLogging = (WrappedComponent) => {
        return class extends React.Component {
          render() {
            return <WrappedComponent {...this.props} />;
          }
        };
      };
      ```

44. **Context API vs Redux**
    - **Answer**: Context API is simpler for small state management, while Redux is more powerful for complex state management with actions and reducers.
    - **Example**:
      ```jsx
      const MyContext = React.createContext(); // Context API
      const store = createStore(rootReducer); // Redux
      ```

45. **Prop types in React (How to apply validation on props in React)?**
    - **Answer**: Using `PropTypes` to specify the type and requirements of props, helping catch errors during development.
    - **Example**:
      ```jsx
      MyComponent.propTypes = {
        name: PropTypes.string.isRequired,
      };
      ```

46. **What are React mixins?**
    - **Answer**: Mixins are a way to share behavior between components in older React versions, but are now deprecated in favor of HOCs and hooks.
    - **Example**:
      ```jsx
      // Mixins are no longer used in modern React
      ```

47. **What are the different hooks you have used?**
    - **Answer**: Common hooks include `useState`, `useEffect`, `useContext`, `useReducer`, `useMemo`, `useCallback`, and `useRef`, each serving different purposes.
    - **Example**:
      ```jsx
      const [state, setState] = useState(initialState);
      useEffect(() => {
        // effect
      }, [dependencies]);
      ```

48. **What are render props in React?**
    - **Answer**: Render props is a technique for sharing code between components using a prop whose value is a function, allowing dynamic rendering.
    - **Example**:
      ```jsx
      <DataProvider render={(data) => <h1>{data}</h1>} />
      ```

49. **What are the different types of exports and imports?**
    - **Answer**: There are named exports, default exports, and corresponding imports, enabling modular code and reusability.
    - **Example**:
      ```jsx
      // Named export
      export const MyComponent = () => {};

      // Default export
      export default MyComponent;

      // Import
      import MyComponent from './MyComponent';
      ```

50. **What are the differences between `createElement` and `cloneElement` in React?**
    - **Answer**: `createElement` creates a new element, while `cloneElement` clones and potentially modifies an existing element.
    - **Example**:
      ```jsx
      const element = React.createElement('div', null, 'Hello');
      const clonedElement = React.cloneElement(element, { className: 'new-class' });
      ```

51. **When to use `useState` and `useReducer`?**
    - **Answer**: Use `useState` for simple state management, and `useReducer` for more complex state logic involving multiple sub-values or complex state transitions.
    - **Example**:
      ```jsx
      const [state, setState] = useState(0);
      const [state, dispatch] = useReducer(reducer, initialState);
      ```

52. **What is `flushSync` in React?**
    - **Answer**: `flushSync` ensures that state updates are immediately reflected in the DOM, useful for synchronously rendering updates during events.
    - **Example**:
      ```jsx
      import { flushSync } from 'react-dom';
      flushSync(() => {
        setCount(count + 1);
      });
      ```
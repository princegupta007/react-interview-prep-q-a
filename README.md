---

# JavaScript and React Concepts

This repository contains key concepts and examples related to JavaScript and React. It serves as a comprehensive guide to understanding and implementing various features and functionalities in these technologies. Additionally, it includes a section on the most asked interview questions for React developers based on my experience.

## JavaScript Concepts

### Promises

Promises are a key feature in JavaScript for handling asynchronous operations. They represent a value that may be available now, or in the future, or never. Promises provide a cleaner, more manageable way to handle asynchronous operations compared to traditional callback functions.

**Example:**

```javascript
const myPromise = new Promise((resolve, reject) => {
    // Asynchronous operation
    let success = true;

    if (success) {
        resolve('Operation successful');
    } else {
        reject('Operation failed');
    }
});
```

### async/await

- **async Function:** Declaring a function as async allows it to use the await keyword. An async function always returns a Promise. If the function returns a value, the Promise is resolved with that value. If the function throws an error, the Promise is rejected with that error.

- **await Expression:** The await keyword can only be used inside async functions. It pauses the execution of the async function and waits for the Promise to resolve. Once the Promise is resolved, it returns the result. If the Promise is rejected, await throws the rejected value.

**Example:**

```javascript
async function fetchData() {
    try {
        let response = await fetch('https://api.example.com/data');
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.error('Error fetching data:', error);
    }
}
fetchData();
```

### Hoisting

- **var Declarations:** Declaration is hoisted; initialization is not.
- **let and const Declarations:** Declaration is hoisted but not initialized (TDZ).
- **Function Declarations:** Both the name and body are hoisted.
- **Function Expressions and Arrow Functions:** Treated like variables; only the variable declaration is hoisted.
- **Class Declarations:** Hoisted but not initialized (TDZ).

### Lexical Scoping

Lexical scoping (also known as static scoping) refers to how variable names are resolved in nested functions: functions are executed using the scope chain that was in effect when they were defined, not the scope chain in effect when they are called.

**Example:**

```javascript
function outerFunction() {
    const outerVariable = 'I am outside!';

    function innerFunction() {
        const innerVariable = 'I am inside!';
        console.log(outerVariable); // Accessible due to lexical scoping
    }

    innerFunction();
    // console.log(innerVariable); // Uncaught ReferenceError: innerVariable is not defined
}

outerFunction();
```

### Closures

A closure is a feature in JavaScript where an inner function has access to the outer (enclosing) function’s variables even after the outer function has finished executing. Closures are created every time a function is created, at function creation time.

### Scope

- **Global Scope:** Variables declared outside any function or block are accessible everywhere. Declared with var, let, or const outside any function or block. Can be unintentionally created by omitting var, let, or const inside a function.
- **Local Scope:** Variables declared within a function or block are only accessible within that function or block.
  - **Function Scope:** Variables declared with var inside a function.
  - **Block Scope:** Variables declared with let or const inside a block.

### Higher-Order Functions

Higher-order functions are functions that operate on other functions by taking them as arguments or returning them as results. They enable a functional programming style and are a powerful concept in JavaScript. Understanding higher-order functions is fundamental for writing clean, modular, and expressive code.

**Example:**

```javascript
function operate(func, x, y) {
    return func(x, y);
}

function add(a, b) {
    return a + b;
}

function multiply(a, b) {
    return a * b;
}

console.log(operate(add, 3, 4)); // 7
console.log(operate(multiply, 3, 4)); // 12
```

### Synchronous and Asynchronous

- **Synchronous Programming:** Tasks are executed one after the other. Each task waits for the previous one to complete before starting. This can lead to blocking, where a long-running task prevents subsequent tasks from starting.

```javascript
console.log('Task 1');
console.log('Task 2');
console.log('Task 3');

// Output:
// Task 1
// Task 2
// Task 3
```

- **Asynchronous Programming:** Tasks can start before the previous ones complete, and the program can continue running other tasks while waiting for some tasks to finish. This is especially useful for I/O operations like network requests, file reading, or timers.

```javascript
console.log('Task 1');

setTimeout(() => {
   console.log('Task 2');
}, 1000);

console.log('Task 3');

// Output:
// Task 1
// Task 3
// Task 2 (after 1 second)
```

### Callback Hell (nested callback)

**Example:**

```javascript
function getData(dataId, getNextData){
    setTimeout(() => {
        console.log("dataId", dataId);
        if(getNextData){
            getNextData();
        }
    }, 2000);
}

getData(1, () => {
    getData(2, () => {
        getData(3, () => {
            getData(4);
        });
    });
});
```

### Variables

- **let:** Block-scoped, meaning it is only accessible within the block (e.g., {}) it is declared in. Variables declared with let cannot be re-declared within the same scope, which helps prevent accidental re-declarations.

- **const:** Similar to let, const is block-scoped. Variables declared with const are hoisted but not initialized, leading to the same temporal dead zone as let.

- **var:** Function-scoped, meaning it is only accessible within the function it is declared in. If declared outside of any function, it has global scope. Variables declared with var can be re-declared within the same scope without causing an error.

### Temporal Dead Zone

The Temporal Dead Zone (TDZ) is a behavior in JavaScript that affects variables declared with let and const. It refers to the period of time during which these variables exist but are not accessible.

### Arrow Functions

Introduced in ES6 (ECMAScript 2015), arrow functions are a shorthand syntax for writing function expressions in JavaScript. They offer a concise syntax, lexical this binding, and are particularly useful for writing short callback functions and preserving this in nested functions. However, they should be used with an understanding of their limitations, such as the lack of their own this, arguments, and not being suitable as methods in objects when this is needed.

**Example:**

```javascript
const functionName = (parameters) => expression;
```

## React Concepts

### Props & State

- **Props:** Inputs to a React component, passed from the parent component down to the child component. Props are read-only and cannot be modified within the child component. They allow the parent component to pass data or methods to its child components and help in creating reusable components and structuring the component tree.

- **State:** Represents the internal state of a component. It is managed within the component and can be updated using setState. State is mutable and can be changed by the component itself using setState. It holds data that influences the rendering and behavior of the component and allows components to be dynamic and interactive.

### useMemo

useMemo is a hook that allows you to memorize expensive computations so that they are only recomputed when one of their dependencies changes. This can improve the performance of your React application by preventing unnecessary re-renders and recalculations.

**Syntax:**

```javascript
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

### DOM and Virtual DOM (VDOM)

- **DOM (Document Object Model):** A programming interface for web documents. It represents the page so that programs can change the document structure, style, and content.

- **VDOM (Virtual DOM):** An abstraction of the DOM used primarily in libraries like React. It is a lightweight copy of the actual DOM that allows for efficient updates and rendering.

### Controlled and Uncontrolled Components

- **Controlled Components:** Components where React controls the state of the form elements. The value of the form element (like an input field or textarea) is controlled by React state and is updated via state handlers like onChange.

- **Uncontrolled Components:** Components where the form data is handled by the DOM itself. The value of the form element is managed by the DOM through refs, and React does not control or manage the state of these elements directly.

### Lazy Loading

Lazy loading is a technique for loading components only when they are needed, improving the performance of your app.

### Suspense

Suspense allows you to show a fallback component while waiting for some code or data to load, enhancing user experience during loading states.

### Hooks

Hooks are functions that let you use state and other React features in functional components without needing to write a class. They were introduced in React 16.8 and provide a way to "hook into" React state and lifecycle features from functional components.

- **useState:** Allows functional components to manage state. It returns a stateful value (the current state) and a function to update it.

- **useEffect:** Lets you perform side effects in function components. It replaces lifecycle methods like componentDidMount, componentDidUpdate, and componentWillUnmount.

- **useContext:** Provides a way to consume a context (global data) in a functional component.

- **useRef:** Returns a mutable ref object whose .current property is initialized to the passed argument (initial value). It can hold a reference to a DOM element or any mutable value.

- **Custom Hooks:** JavaScript functions whose names start with use and may call other hooks. They let you extract component logic into reusable functions.

### Redux / Flux

- **Redux:** Redux is a predictable state container for JavaScript applications. It helps manage the state of an application in a single, central place and ensures that the state can only be updated in a predictable manner.

- **Flux:** Flux is an application architecture for building client-side web applications. It emphasizes a unidirectional data flow, which makes the app’s state management more predictable.

### Context API

The Context API is a React feature that allows you to share state and other values between components without passing props down manually at every level. It is useful for global data such as themes, user information, or settings.

### Fetch vs Axios

- **Fetch:** Fetch is a built-in JavaScript API for making HTTP requests. It returns a promise that resolves to the response of the request.

- **Axios:** Axios is a promise-based HTTP client for JavaScript, which can be used in both the browser and Node.js. It provides a more robust and feature-rich way to make HTTP requests compared to fetch.

---

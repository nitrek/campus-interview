Question Bank: React
This section contains questions specific to the React library, covering its core concepts, hooks, state management, and ecosystem.
Easy
Question: What is JSX?
Answer: JSX stands for JavaScript XML. It is a syntax extension for JavaScript that allows you to write HTML-like code directly within your JavaScript code. It makes writing React components more intuitive and readable. JSX is not understood by browsers, so it needs to be transpiled into regular JavaScript, typically using a tool like Babel.
For example, const element = <h1>Hello, world!</h1>; is JSX.
Question: What is the difference between props and state?
Answer:
Props (Properties): Props are used to pass data from a parent component to a child component. They are read-only, meaning a child component cannot change its own props. Data flows one way: from parent to child.
State: State is data that is managed within a component. It is mutable and can be changed by the component itself (using useState or this.setState). When a component's state changes, React re-renders the component to reflect the new state. State is private and encapsulated within the component.
Hint: Props are like function arguments (passed from outside). State is like local variables declared inside the function (managed from within).
Question: What is the Virtual DOM?
Answer: The Virtual DOM (VDOM) is a programming concept where a virtual representation of a UI is kept in memory and synced with the "real" DOM. When a component's state changes, React first updates the Virtual DOM. Then, it compares the updated Virtual DOM with a pre-update snapshot of the Virtual DOM (a process called "diffing"). Finally, it uses this "diff" to calculate the most efficient way to update the real browser DOM, applying only the necessary changes instead of re-rendering the entire page. This process makes React applications fast and performant.
Hint: It's a lightweight copy of the real DOM. React makes changes to the copy first, figures out the minimal set of actual changes needed, and then applies them to the real thing.
Medium
Question: Explain the lifecycle of a React functional component with hooks.
Answer: With hooks, the lifecycle is managed using the useEffect hook.
Mounting: When a component is first added to the DOM, it renders for the first time. Any useEffect hook with an empty dependency array [] or no dependency array will run its effect function after this initial render. This is equivalent to componentDidMount in class components.
Updating: A component re-renders whenever its state or props change. After the re-render, useEffect checks the dependencies in its dependency array. If any of the dependency values have changed since the last render, it will run the effect function again. If the dependency array is empty [], the effect runs only on mount.
Unmounting: When a component is removed from the DOM, React runs the cleanup function. The cleanup function is the function that you can optionally return from your useEffect's effect function. This is equivalent to componentWillUnmount and is used to clean up resources like subscriptions or timers.
Hint: Think about the useEffect dependency array:
useEffect(() => { ... }) - Runs after every render.
useEffect(() => { ... }, []) - Runs only once, on mount.
useEffect(() => { ... }, [dep1, dep2]) - Runs on mount AND whenever dep1 or dep2 changes.
The return function inside useEffect is for cleanup.
Question: What are React Hooks? Name a few and explain their use.
Answer: Hooks are functions that let you "hook into" React state and lifecycle features from functional components. They allow you to use state and other React features without writing a class.
useState: Allows you to add state to a functional component. It returns an array with two elements: the current state value and a function to update it.
useEffect: Lets you perform side effects in functional components. This includes things like data fetching, setting up a subscription, or manually changing the DOM. It's a combination of componentDidMount, componentDidUpdate, and componentWillUnmount.
useContext: Allows a component to subscribe to React context without introducing nesting. It's used to avoid "prop drilling" (passing props down through many levels of components).
useRef: Returns a mutable ref object whose .current property is initialized to the passed argument. It can be used to hold a value that doesn't cause a re-render when it changes, or to get direct access to a DOM element.
Follow-up: "When would you use useMemo or useCallback?"
Question: What is "prop drilling" and how can you avoid it?
Answer: Prop drilling is the process of passing props from a parent component down through various child components to a deeply nested component that actually needs the data. This can become cumbersome and makes components less reusable, as they are cluttered with props they don't use themselves but only pass down.
Ways to avoid it:
React Context API: The primary solution. You can create a Context Provider at a high level in the component tree and have any nested component consume the context directly using the useContext hook, without having to pass props through intermediate components.
State Management Libraries: Libraries like Redux, Zustand, or MobX provide a centralized store for your application's state. Components can then connect to this store to get the data they need directly.
Component Composition: Sometimes you can restructure your components to pass components as props (e.g., passing a Sidebar component as a prop to a Layout component) to avoid passing all the Sidebar's data through Layout.
Hint: The problem is passing data through components that don't care about it. The solution is to create a way for the deep component to get the data directly.
Difficult
Question: How does React's reconciliation algorithm (diffing) work?
Answer: Reconciliation is the process through which React updates the DOM. The key is the diffing algorithm, which relies on a few assumptions to be fast:
Different Element Types: If the root elements have different types (e.g., an <a> is replaced by an <img>), React will tear down the old tree and build up the new tree from scratch.
Same Element Types: When comparing two DOM elements of the same type, React looks at the attributes of both, keeps the same underlying DOM node, and only updates the attributes that have changed.
Lists of Elements (Keys): When rendering a list of elements, React needs a way to identify which items have changed, been added, or been removed. This is where the key prop is crucial. When React diffs two lists, it matches the children in the old list with the children in the new list based on their keys. A unique key for each item allows React to efficiently reorder, add, or remove elements without re-rendering the entire list. Without keys, React would have to perform a much slower comparison and might mutate nodes unnecessarily.
Hint: The key prop is the most important part of optimizing list rendering. It tells React "this item is the same as before, just maybe in a different position."
Question: When and why would you use useCallback and useMemo?
Answer: These are optimization hooks that should be used when you have a measurable performance problem, not preemptively.
useMemo: This hook memoizes a value. It takes a function and a dependency array. It will only re-run the function (and thus re-calculate the value) if one of the dependencies has changed. This is useful for avoiding expensive calculations on every render.
Use Case: You have a component that computes a filtered list from a large array. If the original array and filter criteria haven't changed, you don't want to re-compute the filtered list on every re-render. useMemo can cache the result.
useCallback: This hook memoizes a function. It returns a memoized version of the callback function that only changes if one of the dependencies has changed.
Use Case: This is primarily useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders. If you pass a new function instance () => {} to a child component on every render, that child component might re-render needlessly (if it's wrapped in React.memo). useCallback ensures that the child receives the exact same function instance as long as the dependencies don't change.
Hint: useMemo remembers a value. useCallback remembers a function. Both are used to prevent unnecessary work or re-renders.
Question: What are Higher-Order Components (HOCs) and how do they differ from custom hooks?
Answer:
Higher-Order Component (HOC): An HOC is an advanced pattern in React for reusing component logic. It is a function that takes a component as an argument and returns a new component. The new component wraps the original component and can inject additional props or logic into it. Example: A withAuth HOC could wrap a component and only render it if the user is authenticated, otherwise, it redirects.
Custom Hook: A custom hook is a JavaScript function whose name starts with "use" and that can call other hooks. It allows you to extract component logic into reusable functions. Unlike an HOC, a hook doesn't wrap a component; it's just a function you call inside your component to get access to some shared stateful logic.
Differences:
Nature: HOCs are functions that return components (component wrappers). Hooks are functions that you call inside components.
Composition: HOCs wrap components, which can lead to "wrapper hell" (many nested components in the React DevTools). Hooks are just function calls and don't add extra components to the tree.
Logic Sharing: HOCs share logic by injecting props. Hooks share stateful logic directly with the component that calls them. Custom hooks are now the preferred and more idiomatic way to share reusable logic between components in modern React.
Hint: HOCs are a pattern from the class-component era. Custom hooks are the modern, simpler way to achieve the same goal of sharing logic in functional components.

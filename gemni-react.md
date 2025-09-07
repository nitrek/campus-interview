

# **React Question Bank**

This section contains questions specific to the **React library**, covering its **core concepts**, **hooks**, **state management**, and **ecosystem**.

---

## **Table of Contents**

- [**React Question Bank**](#react-question-bank)
  - [**Table of Contents**](#table-of-contents)
  - [**Easy**](#easy)
    - [**What is JSX?**](#what-is-jsx)
    - [**What is the difference between props and state?**](#what-is-the-difference-between-props-and-state)
    - [**What is the Virtual DOM?**](#what-is-the-virtual-dom)
  - [**Medium**](#medium)
    - [**Explain the lifecycle of a React functional component with hooks.**](#explain-the-lifecycle-of-a-react-functional-component-with-hooks)
    - [**What are React Hooks? Name a few and explain their use.**](#what-are-react-hooks-name-a-few-and-explain-their-use)
    - [**What is "prop drilling" and how can you avoid it?**](#what-is-prop-drilling-and-how-can-you-avoid-it)
  - [**Difficult**](#difficult)
    - [**How does React's reconciliation algorithm (diffing) work?**](#how-does-reacts-reconciliation-algorithm-diffing-work)
    - [**When and why would you use useCallback and useMemo?**](#when-and-why-would-you-use-usecallback-and-usememo)
    - [**What are Higher-Order Components (HOCs) and how do they differ from custom hooks?**](#what-are-higher-order-components-hocs-and-how-do-they-differ-from-custom-hooks)

---

## **Easy**

### **What is JSX?**

**Answer:**
JSX stands for **JavaScript XML**. It is a syntax extension for JavaScript that allows you to write **HTML-like code inside JavaScript**.

* Makes React components more intuitive and readable.
* Needs to be **transpiled** by Babel before browsers can understand it.

**Example:**

```jsx
const element = <h1>Hello, world!</h1>;
```

---

### **What is the difference between props and state?**

**Answer:**

* **Props:**

  * Passed **from parent to child**.
  * **Read-only**.
  * Similar to **function arguments**.

* **State:**

  * **Managed inside a component**.
  * **Mutable** (via `useState` or `setState`).
  * Causes **re-render** when updated.

**Hint:** Props = external data; State = internal data.

---

### **What is the Virtual DOM?**

**Answer:**

* **Virtual DOM (VDOM)** is a lightweight copy of the real DOM.
* React updates the **VDOM first**, compares it with the previous version (**diffing**), and then updates only the **changed parts** in the real DOM.
* Improves **performance** by avoiding full page re-renders.

**Hint:** React changes the VDOM first, then applies minimal real DOM updates.

---

## **Medium**

### **Explain the lifecycle of a React functional component with hooks.**

**Answer:**
With **hooks**, lifecycle is controlled using `useEffect`:

* **Mounting:**
  `useEffect(() => {...}, [])` → Runs once (componentDidMount).

* **Updating:**
  `useEffect(() => {...}, [deps])` → Runs when **deps change** (componentDidUpdate).

* **Unmounting:**
  Return cleanup function inside `useEffect` (componentWillUnmount).

**Example:**

```jsx
useEffect(() => {
  console.log("Mounted or updated");
  return () => console.log("Cleanup on unmount");
}, []);
```

---

### **What are React Hooks? Name a few and explain their use.**

**Answer:**
**Hooks** let you use state and lifecycle features in functional components.

* `useState` → Add state to function components.
* `useEffect` → Perform side effects (data fetching, subscriptions).
* `useContext` → Consume context without prop drilling.
* `useRef` → Access DOM elements or store mutable values.

**Follow-up:** *When would you use `useMemo` or `useCallback`?*

---

### **What is "prop drilling" and how can you avoid it?**

**Answer:**

* **Prop drilling:** Passing props through multiple levels of components unnecessarily.
* **Solutions:**

  * React **Context API** (with `useContext`).
  * **State management libraries** (Redux, Zustand, MobX).
  * **Component composition**.

---

## **Difficult**

### **How does React's reconciliation algorithm (diffing) work?**

**Answer:**
React uses **diffing algorithm** with these rules:

* **Different element types** → Replace entire tree.
* **Same element type** → Update attributes only.
* **Lists** → Use `key` prop to identify items and avoid unnecessary re-renders.

**Hint:** `key` is critical for list performance.

---

### **When and why would you use useCallback and useMemo?**

**Answer:**

* **useMemo:** Memoizes a **value** to avoid expensive recalculations.
* **useCallback:** Memoizes a **function** to avoid unnecessary re-creations.

**Use Cases:**

* **useMemo:** Expensive computations (filtering large lists).
* **useCallback:** Prevent unnecessary re-renders of memoized child components.

**Hint:** useMemo → value; useCallback → function.

---

### **What are Higher-Order Components (HOCs) and how do they differ from custom hooks?**

**Answer:**

* **HOC:** Function that **wraps a component** and returns a new component. Used for **logic reuse**.
* **Custom Hook:** Function starting with `use` that encapsulates logic, used **inside components**.

**Differences:**

* HOCs **wrap** components → can cause "wrapper hell".
* Hooks are **just functions** → simpler, preferred in modern React.

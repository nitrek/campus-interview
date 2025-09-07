Here’s your **Node.js Question Bank** reformatted in **Markdown** with a **Table of Contents** for easy navigation:

---

# **Node.js Question Bank**

This section contains questions specific to the Node.js runtime environment, covering its architecture, core modules, and common practices.

---

## **Table of Contents**

- [**Node.js Question Bank**](#nodejs-question-bank)
  - [**Table of Contents**](#table-of-contents)
  - [**Easy**](#easy)
    - [**What is Node.js?**](#what-is-nodejs)
    - [**What is NPM?**](#what-is-npm)
    - [**What is the purpose of the package.json file?**](#what-is-the-purpose-of-the-packagejson-file)
  - [**Medium**](#medium)
    - [**Explain the Node.js event loop.**](#explain-the-nodejs-event-loop)
    - [**What is the difference between require() and import?**](#what-is-the-difference-between-require-and-import)
    - [**What is middleware in the context of Express.js?**](#what-is-middleware-in-the-context-of-expressjs)
  - [**Difficult**](#difficult)
    - [**Explain Node.js streams. Why are they useful?**](#explain-nodejs-streams-why-are-they-useful)
    - [**What is the Node.js cluster module and why would you use it?**](#what-is-the-nodejs-cluster-module-and-why-would-you-use-it)
    - [**How would you handle errors in an asynchronous Node.js application?**](#how-would-you-handle-errors-in-an-asynchronous-nodejs-application)

---

## **Easy**

### **What is Node.js?**

**Answer:**
Node.js is an open-source, cross-platform, back-end JavaScript runtime environment that executes JavaScript code outside a web browser. It is built on Google Chrome's V8 JavaScript engine. Node.js allows developers to use JavaScript to write command-line tools and for server-side scripting—running scripts server-side to produce dynamic web page content before the page is sent to the user's web browser.

---

### **What is NPM?**

**Answer:**
NPM stands for **Node Package Manager**. It is the default package manager for Node.js and is the world's largest software registry.
It consists of two main parts:

* A **CLI tool** for installing, updating, and managing software packages.
* An **online registry** of open-source packages that developers can use in their projects.

The `package.json` file in a project root lists the project's dependencies, which NPM can then install.

---

### **What is the purpose of the package.json file?**

**Answer:**
The `package.json` file is the **manifest file** for a Node.js project. It serves several purposes:

* Lists the packages (dependencies) your project depends on.
* Specifies the versions of dependencies.
* Defines scripts (e.g., `npm run start`).
* Provides metadata (name, version, author, license).

It is central to managing a project's dependencies and making the build reproducible.

---

## **Medium**

### **Explain the Node.js event loop.**

**Answer:**
The **event loop** is what allows Node.js to perform **non-blocking I/O operations**, despite JavaScript being **single-threaded**.

**How it works:**

* Node.js starts, processes the input script, and begins the event loop.
* Async operations (file read, DB queries) are passed to the **kernel**.
* Once complete, the kernel notifies Node.js, which puts the callback into the event queue.
* The event loop picks callbacks from the queue and executes them.

**Hint:** Node.js has one thread (event loop), which delegates I/O tasks to the OS kernel and processes results when ready.

**Follow-up:**
*What are the different phases of the event loop? (e.g., timers, I/O callbacks, setImmediate, close callbacks)*

---

### **What is the difference between require() and import?**

**Answer:**

* **require()**

  * Part of **CommonJS** module system.
  * **Synchronous**.
  * Can be used anywhere in the code.
  * Example:

    ```javascript
    const express = require('express');
    ```
* **import**

  * Part of **ES Modules** (ESM).
  * **Asynchronous** and supports tree-shaking.
  * Must be at the **top-level**.
  * Requires `"type": "module"` in `package.json` or `.mjs` extension.
  * Example:

    ```javascript
    import express from 'express';
    ```

**Hint:** `require` = old way, `import` = modern ES standard.

---

### **What is middleware in the context of Express.js?**

**Answer:**
Middleware functions are functions that have access to:

* `req` (request object)
* `res` (response object)
* `next` (function to move to next middleware)

**They can:**

* Execute any code.
* Modify request/response objects.
* End the request-response cycle.
* Call the next middleware in the stack.

**Common uses:** Logging, parsing, authentication, error handling, serving static files.

**Hint:** Middleware = checkpoints in the request pipeline.

---

## **Difficult**

### **Explain Node.js streams. Why are they useful?**

**Answer:**
Streams are objects that **read or write data continuously**.

Types of streams:

* **Readable:** `fs.createReadStream()`
* **Writable:** `fs.createWriteStream()`
* **Duplex:** Both readable and writable (e.g., TCP socket)
* **Transform:** Duplex + modify data (e.g., `zlib` compression)

**Why useful:**

* Handle **large data efficiently** without loading entire data into memory.
* Example: Streaming a video file instead of loading it completely.

**Hint:** Like watching a movie online instead of downloading it first.

**Follow-up:**
*What is the difference between flowing mode and paused mode?*

---

### **What is the Node.js cluster module and why would you use it?**

**Answer:**

* Node.js is **single-threaded** and cannot use multiple cores by default.
* **Cluster module** lets you create **multiple worker processes** that share the same port.
* A **master process** manages workers and distributes requests (round-robin).

**Why use it:**

* Leverage **multi-core CPUs** for better performance.
* Fault tolerance (workers can be restarted if they crash).

**Hint:** Built-in load balancer for Node.js processes.

**Follow-up:**
*How does the cluster module share a port between multiple processes?*

---

### **How would you handle errors in an asynchronous Node.js application?**

**Answer:**
Two main patterns:

* **Callbacks (Error-first pattern):**

  ```javascript
  fs.readFile('/foo.txt', (err, data) => {
    if (err) {
      console.error('Error reading file:', err);
      return;
    }
    console.log(data);
  });
  ```
* **Promises / async-await:**

  ```javascript
  async function readFile() {
    try {
      const data = await fs.promises.readFile('/foo.txt');
      console.log(data);
    } catch (err) {
      console.error('Error reading file:', err);
    }
  }
  ```

Also handle:

* `uncaughtException`
* `unhandledRejection`

**Hint:** Use **async/await + try...catch** for modern error handling.
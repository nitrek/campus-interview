Question Bank: Node.js
This section contains questions specific to the Node.js runtime environment, covering its architecture, core modules, and common practices.
Easy
Question: What is Node.js?
Answer: Node.js is an open-source, cross-platform, back-end JavaScript runtime environment that executes JavaScript code outside a web browser. It is built on Google Chrome's V8 JavaScript engine. Node.js allows developers to use JavaScript to write command-line tools and for server-side scripting—running scripts server-side to produce dynamic web page content before the page is sent to the user's web browser.
Question: What is NPM?
Answer: NPM stands for Node Package Manager. It is the default package manager for Node.js and is the world's largest software registry. It consists of two main parts:
A command-line interface (CLI) tool for installing, updating, and managing software packages.
An online registry of open-source packages that developers can use in their projects.
The package.json file in a project root lists the project's dependencies, which NPM can then install.
Question: What is the purpose of the package.json file?
Answer: The package.json file is the manifest file for a Node.js project. It serves several purposes:
It lists the packages (dependencies) your project depends on.
It specifies the versions of dependencies to use.
It allows you to define scripts that can be run with npm run <script-name> (e.g., for starting the server, running tests).
It provides metadata about the project, like its name, version, author, and license.
It is central to managing a project's dependencies and making the build reproducible.
Medium
Question: Explain the Node.js event loop.
Answer: The event loop is what allows Node.js to perform non-blocking I/O operations, despite JavaScript being single-threaded.
When Node.js starts, it initializes the event loop, processes the provided input script (or drops into the REPL), which may make async API calls, schedule timers, or call process.nextTick(), then begins processing the event loop.
The event loop is a constantly running process that checks a queue for pending events. When an asynchronous operation (like reading a file from a disk or making a database query) is initiated, Node.js passes that operation to the underlying system's kernel. The kernel handles the operation in the background on its own threads. Once the operation is complete, the kernel informs Node.js, which then places the corresponding callback function into an event queue. The event loop continuously picks up these callbacks from the queue and pushes them onto the call stack to be executed.
Hint: Node.js has one thread (the event loop). It acts like a manager that gives I/O tasks to workers (the OS kernel). When a worker finishes, it puts the result in a queue, and the manager (event loop) processes it when it has time. This is why one thread can handle many connections.
Follow-up: "What are the different phases of the event loop? (e.g., timers, I/O callbacks, setImmediate, close callbacks)"
Question: What is the difference between require() and import?
Answer:
require(): This is part of the CommonJS module system, which is the original and traditional way of including modules in Node.js. It is synchronous, meaning it loads modules one by one during execution. You can call require() anywhere in your code.
Example: const express = require('express');
import / export: This is part of the ES Modules (ESM) standard, which is the official standard for JavaScript. It is asynchronous and more performant because modules can be loaded in parallel. import statements are "hoisted," meaning they must be at the top level of a file. To use ES Modules in Node.js, you typically need to name your files with .mjs or set "type": "module" in your package.json.
Example: import express from 'express';
Hint: require is the old, synchronous way. import is the new, asynchronous, standardized way. Modern Node.js supports both.
Question: What is middleware in the context of Express.js?
Answer: Middleware functions are functions that have access to the request object (req), the response object (res), and the next function in the application's request-response cycle. The next function is a function in the Express router which, when invoked, executes the middleware succeeding the current middleware.
Middleware functions can:
Execute any code.
Make changes to the request and the response objects.
End the request-response cycle.
Call the next middleware in the stack.
Common middleware tasks include logging requests, parsing the body of incoming requests (e.g., express.json()), handling authentication and authorization, and serving static files.
Hint: Think of middleware as a series of checkpoints or processing stations that a request goes through on its way to the final route handler. Each station can inspect or modify the request before passing it to the next one.
Difficult
Question: Explain Node.js streams. Why are they useful?
Answer: Streams are objects that let you read data from a source or write data to a destination in a continuous fashion. In Node.js, there are four types of streams:
Readable: Streams from which data can be read (e.g., fs.createReadStream).
Writable: Streams to which data can be written (e.g., fs.createWriteStream).
Duplex: Streams that are both Readable and Writable (e.g., a TCP socket).
Transform: Duplex streams that can modify or transform the data as it is written and read (e.g., a zlib compression stream).
Why they are useful: Their primary advantage is memory efficiency. Instead of reading an entire large file into memory before processing it (which could crash your application), you can read it and process it in small chunks (buffers) of data. This allows you to handle very large data sources with a small, fixed amount of memory. A common use case is piping a readable stream (like a file read) into a writable stream (like an HTTP response).
Hint: Think of streaming a movie online. You don't download the entire movie before you start watching. You watch it chunk by chunk as it arrives. Node.js streams do the same for data.
Follow-up: "What is the difference between a stream in flowing mode vs. paused mode?"
Question: What is the Node.js cluster module and why would you use it?
Answer: Since a single Node.js instance runs in a single thread, it cannot take advantage of multi-core systems by default. The cluster module is a core Node.js module that allows you to easily create child processes that all share server ports.
It works by creating a master process that can fork multiple worker processes. The master process does not handle requests itself but distributes incoming connections among the worker processes in a round-robin fashion. Each worker process is its own Node.js instance with its own event loop.
Why use it: This allows a Node.js application to scale across all available CPU cores on a machine, significantly increasing the number of requests it can handle concurrently. It also provides resilience; if one worker process crashes, the master process can fork a new one to replace it without the entire application going down.
Hint: It's Node's built-in way to multiply itself to use all the CPU cores on a server, acting like a load balancer for its own child processes.
Follow-up: "How does the cluster module share a port between multiple processes?"
Question: How would you handle errors in an asynchronous Node.js application?
Answer: Handling errors in async code is crucial. There are two main patterns:
Callbacks (The "Error-First" Pattern): This is the traditional pattern. Asynchronous functions take a callback function as their last argument. This callback is invoked with its first argument being any error that occurred, and subsequent arguments being the result data. You must always check for the error argument first.
fs.readFile('/foo.txt', (err, data) => {
  if (err) {
    console.error('Error reading file:', err);
    return;
  }
  // process data
});


Promises and async/await: This is the modern and preferred approach. Asynchronous functions return a Promise. You can handle errors by chaining a .catch() block to the promise chain or, more cleanly, by using async/await within a try...catch block.
async function readFile() {
  try {
    const data = await fs.promises.readFile('/foo.txt');
    // process data
  } catch (err) {
    console.error('Error reading file:', err);
  }
}


It's also important to handle uncaught exceptions and unhandled promise rejections at the process level to prevent the application from crashing silently or being left in an unstable state.
process.on('uncaughtException', (err) => { ... });
process.on('unhandledRejection', (reason, promise) => { ... });


Hint: For modern Node.js, always prefer async/await with try...catch as it makes asynchronous error handling look and behave like synchronous code, which is much easier to read and reason about.

only reformat this as markdown , also add table of content
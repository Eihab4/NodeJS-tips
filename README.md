# Node.js and JavaScript Overview

## ECMAScript

- **ECMAScript 6**: Introduced in 2015.
- **ECMAScript vs. JavaScript**: ECMAScript is a standardized specification for scripting languages, while JavaScript is an implementation of this specification.

## JavaScript Engine and Node.js

- **JavaScript Engine**: JavaScript code needs to be processed and executed by a JavaScript engine to be understood and run on a computer.
- **V8 Engine**: The V8 engine sits at the core of Node.js and is developed by Google. It is written in C++.
- **Just-In-Time (JIT) Compiler**: Some engines, like V8, use a JIT compiler to optimize and convert parts of JavaScript code into machine code for faster execution.
- **Node.js**: Node.js is much more than just a C++ application; it is a runtime environment that includes the JavaScript engine and additional components.

## JavaScript Runtime Environment

- **Runtime Environment**: The JavaScript runtime environment provides all the necessary components outside of the browser.
- **REPL**: Node.js includes a Read-Eval-Print Loop (REPL) for interactive programming.

## Modules in Node.js

### Types of Modules

1. **Local Modules**: Custom modules created for your application.
2. **Built-in Modules**: Modules that come with Node.js.
3. **Third-Party Modules**: Modules installed via npm.

### Module System

- **Require**: When using `require()`, you don't have to include the `.js` extension.
- **Module Isolation**: Each file in Node.js is treated as a module and is isolated by default.
- **CommonJS**: CommonJS is a module standard used in Node.js to manage module inclusion. Use `module.exports` for default exports.

### Module Caching

- **Caching**: Node.js caches modules after the first load. Subsequent `require` calls retrieve the cached module rather than reloading it.

### Default Export

- **Default Export**: Use `module.exports` to export a module's functionality so it can be used in other files.

## Built-in Modules

- **Path Module**: Provides utilities for working with file and directory paths.
- **File System Module**: Used for interacting with the file system, including reading and writing files.

## Streams

- **Streams**: Built-in modules for handling data transfer in chunks, which is memory-efficient and time-saving.

### Pipes

- **Practical Applications**:
  - **File Compression**: Using pipes with `zlib` for compressing files.
  - **HTTP Requests**: Handling HTTP request and response streams in web servers.
  - **Data Transformation**: Applying transformations to data streams, such as encoding or decoding.

- **Advantages**:
  - **Memory Efficiency**: Pipes are more memory-efficient than reading the entire data into memory.
  - **Simplified Code**: Pipes simplify the process of handling stream data.

## HTTP Module

- **HTTP Module**: Provides functionality for creating HTTP servers and handling HTTP requests and responses.

## Node.js Runtime

- **Components**:
  1. JavaScript Library
  2. C++ Features (e.g., file reading/writing, networking)
  3. Dependencies

## Libuv

- **Overview**: Libuv is a cross-platform open-source library written in C, handling asynchronous non-blocking operations in Node.js.
- **Key Components**:
  - Thread Pool
  - Event Loop
- **Thread Pool**: Contains a default of 4 threads, which can be increased based on the machine's core count.
- **Async Handling**: Libuv handles asynchronous methods using native mechanisms and a thread pool.

## Execution Order

1. **Execute Synchronous Code**: Runs any synchronous code in the stack.
2. **Execute `nextTick` Callbacks**: Executes `process.nextTick()` callbacks.
3. **Execute Microtasks (Promise Callbacks)**: Processes microtasks in the microtask queue.
4. **Timers**: Processes timers (e.g., `setTimeout`, `setInterval`) if their scheduled time has been reached.
5. **I/O Callbacks**: Handles I/O callbacks for file operations, network requests, etc.
6. **Check Phase**: Processes `setImmediate()` callbacks.
7. **Close Callbacks**: Handles callbacks for closed handles (e.g., socket `close` events).

- **Note**: The execution of `setTimeout` with a 0 delay is not guaranteed to occur before or after I/O callbacks.


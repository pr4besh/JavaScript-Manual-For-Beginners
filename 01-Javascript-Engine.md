**Table of Content**

- [JavaScript Engine](#javascript-engine)
  - [How engine works? (Summary)](#how-engine-works-summary)
  - [Inside the JavaScript Engine](#inside-the-javascript-engine)
    - [Compilation](#compilation)
    - [Interpretation](#interpretation)
  - [Just in Time (JIT) compilation in JavaScript](#just-in-time-jit-compilation-in-javascript)
  - [Call Stack and Memory Heap](#call-stack-and-memory-heap)
    - [Call Stack](#call-stack)
    - [Memory Heap](#memory-heap)
    - [Stack vs Heap](#stack-vs-heap)
      - [References in JavaScript](#references-in-javascript)
      - [Garbage Collection](#garbage-collection)
  - [Execution Context](#execution-context)
    - [Types of Execution Context](#types-of-execution-context)
    - [Execution Stack](#execution-stack)
      - [Creation of Execution Stack](#creation-of-execution-stack)
    - [Lexical Environment](#lexical-environment)

# JavaScript Engine

JavaScript engine is a software or a program responsible to run our JavaScript code. Almost every modern day browsers we use have their own JavaScript engine running in the background. Some of the most popular JavaScript engine are -

- **v8** - Developed by **Google\_** for **Chrome**
- **SpiderMonkey** - Developed by **_Mozilla_** for **Firefox**
- **JavaScriptCore** - Developed by **_Apple_** for Safari
- **Chakra** - Developed by **_Microsoft_** for **Edge**

**_Brendan Eich is the creator of JavaScript language and the co-founder of Mozilla project._**

## How engine works? (Summary)

- The engine parses/read the script.
- Then the script is compiled into machine code.
- Then, the machine runs the code.

## Inside the JavaScript Engine

Computers can only understand binary (0s and 1s) which is the reason our computer program needs to be converted into binary which is also called machine code. We convert our program into machine code via compilation or interpretation.

#### Compilation

During compilation, the entire source code is converted into machine code all at once. The code is written into a portable file that can be executed anywhere- regardless of platform or operating system. The program is first converted into machine code and later executed on the machine. The execution of the machine code happens right after the compilation.

#### Interpretation

During interpretation, the interpreter runs through the source code and executes it line by line. The code is read and executed at the same time. The conversion of code into machine code does not happen of time, instead, right before execution. Interpreted programming language are much slower in terms of performance when compared to compiled language.

## Just in Time (JIT) compilation in JavaScript

Although most people consider JavaScript as an interpreted language, that is no longer the case. Modern JavaScript use the concept of both compilation and interpretation at the same time knows as **_Just-In-Time (JIT) Compilation_**.

In this approach, whole program gets compiled into machine language at once and then it is executed. Unlike the compiled language like C, where the compilation is done ahead of time (before actual execution of code), with JavaScript, the compilation is done during execution.

## Call Stack and Memory Heap

### Call Stack

JavaScript is a single-threaded language i.e. it has only one call stack and it can process one statement at time. The call stack keeps track of functions to be executed. Call Stack follows the **Last in, First Out** principle which means it always process the call on top of the stack at first.

When a function is called, it is added to the stack. When a function calls another function, it's added on top of the calling function.

```js
const greet = () => {
  sayHello();
  console.log("I am a robot.");
};

const sayHello = () => {
  console.log("Hello");
};

greet();
```

To summarize, - At first, greet() is added to the call stack. - greet() then calls sayHello() function and adds sayHello() to the call stack.

At this point, the call stack status is currently -

+++++++++++++++++++<br>
Call Stack<br>
+++++++++++++++++++<br>
sayHello()<br>
greet()<br>
+++++++++++++++++++<br>

sayhello() is now at the top of the stack and is executed. It prints out **Hello** to the console and is removed from the stack.

+++++++++++++++++++<br>
Call Stack<br>
+++++++++++++++++++<br>
greet()<br>
+++++++++++++++++++<br>

Now, greet() is at the top of the stack and prints out **I am robot** to the console and thus removed from the stack.

The call stack is empty now and the final output would look like this:

```js
"Hello";
"I am a robot.";
```

### Memory Heap

JavaScript stores objects and functions in heap. Unlike stack, JavaScript engine doesn't allocate a fixed memory for these objects. Instead, more spaces will be allocated as needed. This is called the **dynamic memory allocation.**

### Stack vs Heap

**Stack**

- Primitive values and references
- Size is known at compile time
- Allocates a fixed amount of memory.

**Heap**

- Objects and functions
- Size is known at run time
- No size limit per object

**Examples**

```js
const myProfile = {
  firstName: "Prabesh",
  lastName: "Thapa",
  age: 23,
};
```

**JavaScript allocates memory for this object in stack.**
**_But the actual values of the objects are still primitive. Hence, they are stored in stack._**

```js
const hobbies = ["anime", "football", "cricket"];
```

**Arrays are objects as well in JavaScript. Hence, they are stored in heap.**

#### References in JavaScript

All variables first point to stack. If it is not primitive value, the stack contains a reference to the object in the heap.

#### Garbage Collection

JavaScript not only allocate memory for objects, they also release the memory. Once the variable or a function is nor required anymore, JavaScript releases the memory it occupied.

## Execution Context

Execution Context is an concept of an environment where JavaScript code is evaluated and executed.

### Types of Execution Context

- **Global Execution Context** : This is the default execution context. It does two thing: **_creates a global object (window object) and sets the value of *this* to global object._**

- **Functional Execution Context** : New execution context is created every time a function is invoked. Every function has their own execution context, but they are created only when the function is called.

### Execution Stack

JavaScript engine creates a global execution context and pushes it to the current execution stack. When the engine finds the function invocation, it creates a new execution context for that function and pushes it at the top of stack. The engine executes the function which is at the top of stack and removes it from the stack once the execution of that function is completed.

#### Creation of Execution Stack

The execution stack is created in two phase:

1. **LexicalEnvironment** is created.
2. **VariableEnvironment** is created.

```js
ExecutionContext = {
	LexicalEnvironment = <reference to LexicalEnvironment in memory>,
	VariableEnvironment = <reference to VariableEnvironment in memory>,
}
```

### Lexical Environment

Lexical Environment is a structure that holds identifier-variable mapping. (_identifier refers to name of variables/functions and the variable is reference to actual object including function object and array object_).

Example:

```js
var a = 10;
var b = 20;

function foo() {
  console.log("bar");
}
```

The lexical environment for above code loos like this:

```js
LexicalEnvironment = {
	a:10,
	b:20,
	foo: <reference to foo function in memory>
}
```

Each Lexical Environment has three component:

- Environment Record
- Reference to outer environment
- _this_ binding

[Next [JavaScript Variables] -->](./02-All-About-Variables.md)

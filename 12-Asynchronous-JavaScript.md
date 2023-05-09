# Understanding Asynchronous JavaScript

JavaScript is single-threaded programming language which means only one thing can happen at a time. This helps us to simplify our code but this also means that we can't perform long operations such as reading from a file without blocking the main thread. That's where asynchronous JavaScript helps us.

Asynchronous JavaScript helps us to perform tasks without having to wait for a pervious task to complete, which results in a faster and more efficient code execution. When we use asynchronous programming, the browser will continue to render the page while the task is running in the background. This means that the user will not have to wait for the task to finish before they can interact with the webpage.

Before we dive into asynchronous JavaScript, we need to first understand how synchronous JavaScript gets executed by JavaScript engine.

_Reminder:_

```
**Execution Context**: abstract concept of environment where JavaScript code is evaluated and executes.

**Call Stack**: used to store all the execution context created during the code execution.
```

Let us consider a example.

```js
const second = () => {
    console.log("This is second function.")
}

const first = () => {
    console.log("This is first function.")
    second();
    console.log("End);
}

first();
```

When this code is executed, a gloval execution context `main()` is created and pushed to the top of call stack.

```
|           |
|           |
|  main()   |
|___________|
```

The `first` and `second` functions are then added to the global memory. The `first` function is called within the main function and the cal to `first` function is added to the top of call stack.

```
|           |
| `first()` |
|___________|
```

The `first` function is executed and logs "I am the first function." to the console. The `second()` is called within the `first` function so, the `second()` is added to the top of the call stack.

```
|           |
|  second() |
|  first()  |
|___________|
```

The `second` function is also executed and logs "This is the second fucntion." to the console. The call to the `second()` is then removed form the call stack.

```
|           |
|           |
|  first()  |
|___________|
```

The `first` function then logs "End" to the console and the call to the `first` function is also removed from the call stack. The `main()` function or global execution context finishes executing and is removed from the stack.

```
Note: Call Stack is Last In, First Out (LIFO) data structure, that means that the last function to be added to the stack is the first one to be removed.
```

**_Problem caused by Synchronous behavior of JavaScript:_**

One common problem caused by this synchronous behavior of JavaScript is that it can block the browser's user interface and make it unresponsive. This happens when a time-consuming tasks such as fetching data from server is executed synchronously on the main thread.

```js
const processImage = (img) => {
  console.log("Processing " + img);
};

const downloadImage = (url) => {
  setTimeout(() => {
    console.log("Downloading Image from " + url);
  }, 2000);
};

downloadImage("www.someimage.com");
processImage("Poo.jpg");
```

_Output:_

```
Processing Poo.jpg
Downloading Image from www.someimage.com
```

This is something we do not expect because the `process()` function gets executed before the `download()` function. We would expect image to be downloaded before we process it.

To avoid such problems, we can use asynchrnous programming concepts such as `callbacks`, `promises`, and `async/await` to allow long-running tasks to be executed in the background without blocking the UI.

**_So, How does Asynchronous JavaScript work?_**

## Callbacks

We can pass a fucntion to another function as an argument in JavaScript. By definition, `callback` is a function that we pass into another function as an argument for executing later when the execution of first function is completed.

Let us consider an example where a function accepts an array of number as argument and returns a new array of odd numbers.

```js
function filterOdd(numbers) {
  let results = [];
  for (const number of numbers) {
    if (number % 2 != 0) {
      results.push(number);
    }
  }
  return results;
}

let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
console.log(filterOdd(numbers)); // Output: [1,3,5,7,9]
```

In this example, we have a function that accpets an array of numbers and returns new array of odd numbers. But if we want to return an array of even numbers, we now need to modify the `filterOdd` function. This is not an ideal condition.

We need to make our function more generic and resuable. We can do so by extracting the logic in `if` block and wrap it in a new function and pass the `filter` function as an argument.

```js
function isOdd(number) {
  return number % 2 !== 0;
}

function filter(numbers, callback) {
  let results = [];
  for (const number of numbers) {
    if (callback(number)) {
      results.push(number);
    }
  }
  return results;
}

let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
console.log(filter(numbers, isOdd)); // Output: [1,3,5,7,9]
```

We get the same output as previous one but now with the updated code, we can pass any function that accepts an argument and returns a boolean value to the second argument of the `filter` function.

For example, we can now use this `filter` function to return an array of even numbers too.

```js
function isOdd(number) {
  return number % 2 !== 0;
}

function isEven(number) {
  return number % 2 === 0;
}

function filter(numbers, callback) {
  let results = [];
  for (const number of numbers) {
    if (callback(number)) {
      results.push(number);
    }
  }
  return results;
}

let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];

console.log(filter(numbers, isOdd)); // Output: [1,3,5,7,9]
console.log(filter(numbers, isEven)); // Ouput: [2,4,6,8]
```

Here, `isOdd` and `isEven` are callback functions or callbacks.

### Synchronous Callbacks

Synchronous callbacks is a callback function that is exeucuted immediately when it is called, blocking the main thread until it completes. Synchronous callbacks are executed in the same order as they are called, and they can cause the program to become unresponsive if they take too long to complete.

The `isOdd` and `isEven` are examples of synchronous function because they execute immediately during the execution of `filter()` function.

### Asynchronous Callbacks

Asynchronous callbacks are the functions that are executed after the execution of high-order function that uses the callback. This allows us to write a non-blocking code that will execute the rest of the code if it has to wait for certain operation to complete. This helps us to execute long-running operations without freezing the UI or blocking the execution of other code.

Let us consider example from previous where we wrote a program to download a picture and process it. Downloading a picture takes time depending upon the speed and size of the picture. This may halt or slow down our program as we seen before.

To resolcve such issues, we can update our code as below -

```js
function downloadImage(url, callback) {
  setTimeout(() => {
    // download image
    console.log("Downloading image from " + url);
    // process image after download
    callback(url);
  }, 1000);
}

function process(picture) {
  console.log("Processing " + picture);
}

downloadImage("www.someimage.com/foo.jpg", process);
```

_Output:_

```
Downloading image from www.someimage.com/foo.jpg
Processing www.someimage.com/foo.jpg
```

In this example, we call the `downloadImage` function with a URL and a `process()` callback function which downloads the image from the URL. However, downloading an image can take some time, so we don't want the function to block the execution of the code. Therefore, we set a timeout of 1 second (1000 milliseconds) to `downloadImage()` function.

Once the image is downloaded, the `callback` function is called with the url of the downloaded image as an argument. In this case, the `callback` fucntion is the `process` function. The `process` function is executed asynchronously, after the image is downlaoded and the `callback` fucntion is called.

_Note_: `setTimeout` is not a part of JavaScript engine but it is a part of Web APIs (in browsers).

# Functions

A `function` is a block of code that runs when the function is called.

Syntax:

```
function functionName(paramter1, paremeter2, ...., parameterN) {
    // Block of Code
}
```

To declare a function, we use a `function` keyword followed by the name of the fucntion which is followed by thr `parrameter` enclosed in `()` followed by pair of curly braces `{}` which covers the block of code to be executed.

We can call (invoke) a function just with the name of fucntion followed by `()`.

```
functionName();
```

There are times when function require additional data to work in the form of `arguments`. Arguments are values passed on to functions when calling the fucntions inside the pair of parentheses `()`.

Although, `parameter` and `arguments` are often understood to be same, they have slightly different meanings.

A parameter is a variable that the function expects to receive as input in order to perform the specified tasks.

```js
function findSum(a, b) {
  return a + b;
}
```

Here, `a` and `b` are the paremeters of `findSum` function.

Arguments is a value that is passed to function when it is called. They are the actual values that are used to replace the paremeter in a fucntion.

```js
let result = findSum(2, 3);
console.log(result); //OUTPUT: 5
```

Here, 2 and 3 are the arguments passed to `findSum` function. The value 2 is passed as argument for the `a` parameter while value 3 is passed as argument for `b` paremeter.

## Function Declarations and Function Expression

We have two ways to create functinos in JavaScript: `function declaration` and `function expression`.

Function declaration is a way to create a named fucntion using `function` keyword like we mentioned above.

Function expression on other hand is a way to create anonymous function that can be assigned to variable or passed as an argument to another function.

Example:

```js
var greet = function (name) {
  console.log("Hello" + name + "!");
};
```

This creates a function expression that assigns the anonymous function to the variable `greet`. This function takes one parameter named `name` and logs a greeting message with the name passed as an argument.

The most important difference between function expression and function declaration is that we can define a function without a name in function expression.

### Difference between function declaration and function expression

One key difference between function declaration and function expression is that fucntion declarations are hoisted to the top of their scope, which means they can be called before they are defined. On other hand, function expressions are not hoisted and cannot be called before they are defined.

What is `hoisting` you may ask if you have already forgotten.

```
Hoisting is the behavior where variables and functions are moved to top of their respective scopes during compilation before the code is actually executed.
```

So, what does all this means?

This means that the following code will work absolutely fine without problems.

```js
console.log(sum(2, 4)); //OUTPUT: 6

function sum(a, b) {
  return a + b;
}
```

Although, we are calling the `sum()` function before defining it, we do not get any error - thanks to function hoisting.

However, we must always remember that hoisting is limited to function declaration - **NOT TO FUNCTION EXPRESSION**

Example:

```js
console.log(sum(2, 4));

var sum = function (a, b) {
  return a + b;
};
```

```
OUTPUT:
Uncaught TypeError: sum is not a function
```

This code throws an error because of hoisting in JavaScript. When a variable is declared using the `var` keyword, its declaration is hoisted to the top of its scope during compilation, but its initialization is not. This means that the variable sum is being hoisted to the top of its scope, but it is still undefined at the point where it is called in the `console.log` statement.

## Function Parameters

There are two kinds of parameter syntax: `default paremeter` and `rest parameter`.

### Default Parameter

In JavaScript, parameters of a function defaults to `undefined`. It means that if no arguments is passed to the function, its parameter wil have the default value od `undefined`.

Example:

```js
function greet(name) {
  console.log("Hello " + name);
}

greet(); //OUTPUT: Hello undefined
```

Here, the `greet()` function takes the `name` parameter but we did not pass any arguments to the function, hence the value of `name` parameter is set to `undefiend`.

However, we can set that to a different default value. ES6 provides us easier ways to set default values to the parameter. We use the assignment operator `=` and the default value after the parameter name to set a default parameter.

```js
function greet(name = "User") {
  console.log("Hello " + name);
}

greet(); // OUTPUT: Hello User
greet("Prabesh"); //OUTPUT: Hello Prabesh
```

### Rest Parameter

The rest parameter syntax `...` allows us to accept indefinite number of arguments as an array. It is used as a prefix of the function's last parameter.

_Example:_

```js
function userInfo(firstName, lastName, ...otherInfo) {
  return otherInfo;
}
```

The rest operator `...` accepts the rest of user-specified arguments as an array and assign that array to the `otherinfo` parameter.

Now,we caninvoke the function with as many arguments as we like.

```js
userInfo("Prabesh", "Thapa", 23, "entry", "Web Developer");
```

This invocation will return an array of the argumnets other than the values "Prabesh" and "Thapa" that got assigned to `firstName` and `lastName` parameters.

_OUPUT:_

```
[23, "entry", "Web Developer"]
```

### Difference Between Arguments and Rest Parameter

- **`arguments` object is an array-like object - not a real array.**: JavaScript arguments object is array-like object that does not have comprehensive features of regular arrays but the rest parameteris a real array object we can call use all kind of array methods on it.

- **We cannot use `arguments` object in arrow function**: The `arguments` object is not available within arrow functions but we can use arrow functions in rest parameters.

## Arrow Functions

The second way we can declare the function is with arrow functions which was made available in ES2015.

_Example:_

```js
const greet = (name) => {
  console.log("Hello " + name);
};
```

You may be wondering while both the regular and arrow syntaxes define functions, when would you use one or another?

We will learn more about the arrow functions and how they differ from normal function delcarations when we understand **`this`** keyword in next section.

## Function Scope

A function creates a scope so that variables defined within the function cannot be accessed outside the function or within other functions.

```js
function myFunction() {
  let var1 = "something";
  console.log(var1);
}

console.log(x); //OUTPUT: x is not defined
```

### Lecxical Scoping

Lexical scoping is a key concept in JavaScript that determines how variables and functions are accessed within nested scopes, based on their position in the code.

In JavaScript, every time you create a new function, it creates a new scope. When you reference a variable or function within a particular scope, JavaScript looks for it first within that scope. If it can't find it there, it looks in the next outer scope, and so on until it reaches the global scope.

This means that variables and functions declared in an outer scope can be accessed by inner scopes, but variables and functions declared in an inner scope cannot be accessed by outer scopes.

```js
function myFunction() {
  var outerVar = "Outer Scope";

  function innerFunction() {
    var innerVar = "Inner Scope";
    console.log(outerVar); // Accessible from inner scope
  }

  innerFunction();
  console.log(innerVar); // Not Accessible from outer scope
}

myFunction();
```

In the example above, `myFunction` creates a new scope that has `outerVar` variable and `innerFunction` function. `innerFunction()` creates a new scope that has `innerVar` variable. When `innerFunction()` is called, it logs the value of `outerVar` which is in outer scope but we will get an error when we try to log the value of `innerVar` because it is not accessible outside the inner scope.

## IIFEs

`Immediately Invoked Function Expression` or IIFEs is a design pattern to protect the scope of our functions and the variables within (create a private scope).

An IIFE is created by wrapping a function in parentheses and immediately invoking it.

_Example:_

```js
(function myFunction() {
  //code block
})();
```

When the code is executed, the function is immediately invoked and its code in executed. This means that any variables and functions defined within the function are only accessible within the function's scope and do not leak into global namespaces.

Let's declare a normal function.

```js
function getSum() {
  let x = 2;
  let y = 4;
  let sum = x + y;
  console.log(sum);
}

getSum();
```

Here, we have a function that simply adds two variables together and console logs the sum. We then call the function after. But there may be situation where we want to call the function once to get an output and never use it again. Although our variables cannot be accessed outside the function, we would lile to make sure that the function also cannot be accessed globally. **That's where IIFE comes in handy.**

Now, we can rewrite the code as below:

```js
(function () {
  let x = 2;
  let y = 4;
  let sum = x + y;
  console.log(sum);
})();
```

Since, we do not intend to call the function again after the invocation, we do not need to give the function a name anymore.

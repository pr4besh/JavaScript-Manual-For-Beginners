**Table of Content**

# Variables in JavaScript

## Hoisting

Hoisting is the default behavior of JavaScript where it defines all the declarations at the top of scope before code execution. JavaScript only hoists declarations, not initialization.

JavaScript engine treats all variable declarations using _var_ as if they are declared at the top of global scope (if declared outside function) or at the top of functional scope (if declared inside function) regardless of where the actual declaration is made. This simply is **_Hoisting_**.

### Hoisting in var

```js
console.log(name); //OUTPUT: undefined

var name = "Prabesh";

console.log(name); //OUTPUT: "Prabesh"
```

Normally, we would expect to get an error (ReferenceError) in the first _console.log_ since the variable name wasn't already declared before. But JavaScript hoists all variable declarations at the top.

**Behind the Scene in interpreter**

```js
//variable declaration gets hoisted at top
var name;

console.log(name); //OUTPUT: undefined

name = "Prabesh";

console.log(name); //OUTPUT: "Prabesh"
```

_In JavaScript, undeclared variable is assigned as type of undefined while ReferenceError is thrown when trying to access undeclared variable._

**Hoisting in Functional Scope**

Variables declared within function are in the local scope. variables in the local scope are only accessible within the function in which they are defined. Hence, we can use variable with same name and use it in different function.

If we declare local variable and a global variable with same name, the local variable will take precedence when we use it inside a function. In simple words, local variable shadows global variables.

```js
function getName() {
  console.log(name);
  var name = "Prabesh";
}

getName();

//OUTPUT: undefined
```

**Behind the Scene in interpreter**

```js
function getName() {
  var name;
  console.log(name); //OUTPUT: "Prabesh"
  name = "Prabesh";
}

getName();
```

To avoid such inconvinence, we need to declare and initialize the variable before we use it.

**_Note to Remember: JavaScript declares the variable first in the background, then initialize them._**

ALl of the undeclared variables are global varibles.

```js
// Example of Hoisting
function hoisting() {
  let name = "Prabesh";
  age = 23;
}
hoisting();

console.log(name); // Reference Error: name is not defined.
console.log(age); // Output: 23
```

**So what exactly happened here?**

In the above code, we have a function called hoisting() where we did not declare a variable using let/var/const and another variable declared with let. As mentioned above, _assigning the undeclared variable to the global scope is done by JavaScript_. Hence, age variable is availabe even outsode of scope(globally) but the scope of name variable is within the function, so we get the ReferenceError.

### Hoisting with let/const

In ES6, _let_ does not allow us to use undeclard variables and throws a ReferenceError. This makes sure that we always declare our variable first.

**Example 1:**

```js
console.log(num);
//OUTPUT: ReferenceError: Cannot access 'num' before initialization

let num = 20;

console.log(num); //OUTPUT: 20
```

Let's have a look at another example:
**Example 2:**

```js
console.log(number2);
//OUTPUT: ReferenceError: number2 is not defined.

let number = 20;
```

**_Do you notice something different in example 1 and 2?_**

The error in example 1 says: _ReferenceError: Cannot access 'num' before initialization_ but the error in example 2 is _ReferenceError: number2 is not defined_

The error "is not defined" means our JavaScript engine has no idea what _number2_ variable is because we never defined it.
But the error "cannot access before initialization" means our JS engine knows the "num" variable since "num" is hoisted to the top of global scope.

_To summarize, variables declared with **let** or **const** are hoisted **without** a default initialization but the variables declared with **var** are hoisted **with** default initialization of undefined._

### Temproal Dead Zone

This is a period during execution where _let/const_ variables are hoisted but not accessible.

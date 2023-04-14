**Table of Content**

- [Variables in JavaScript](#variables-in-javascript)
  - [Variable Declarations](#variable-declarations)
  - [Variable Naming Rules](#variable-naming-rules)
  - [Variable Scopes](#variable-scopes)
    - [Global Scope](#global-scope)
    - [Local Scope](#local-scope)
      - [Function Scope](#function-scope)
      - [Block Scope](#block-scope)
  - [Hoisting](#hoisting)
    - [Hoisting in var](#hoisting-in-var)
    - [Hoisting with let/const](#hoisting-with-letconst)
    - [Temproal Dead Zone](#temproal-dead-zone)

# Variables in JavaScript

Variables are simply the identifiers used to store information.

## Variable Declarations

We can create variable in JavaScript with keywords like _let/const/var_.

```js
let name;
var age;
const gravity;
```

We can store some data in these variables using the assignment operator **'='**.

```js
let name;
name = "Prabesh";
```

But the better option would be to combile the variable declarations and assignment in one line.

```js
var age = 23;
```

We can also declare multiple variables in one line.

```js
let name = "Prabesh",
  age = 23,
  nickname = "entry";
```

## Variable Naming Rules

There are basically two rules while naming variable:

1. It must contain only letters(a-z), digits(0-9), or the symbols **$ and \_**.
2. The first character must not be a digit.

**Case Matters** - _Variables with name 'age' and 'AGE' are two different variables._

**Valid Variable Names**

```js
let name = "Prabesh";
let _age = 23;
let $ = 127;
let nickName404 = "entry";
```

**Invalid Variable Name**

```js
let 2name = "My Name"; // Cannot start with digit
let my-name = "My Name"; //hyphens (-) aren't allowed
//Symbols except '$ and _' aren't allowed.
```

## Variable Scopes

When we declare a variable, it cannot just be accessed from anywhere in our code.

### Global Scope

If a variable is available globally, the code can read or modify the variable from anywhere. We can declare the variable globally by declaring it outside the function.

There is only one Global scope throughout our program. When we begin writing our code, we are already in global scope. Something is considered global in JavaScript when the variable is the direct child of our browser's **window** object.

```js
var number = 20; //Global Variable

function addby2() {
  //Local Scope(Function)
  return number + 2; //Global variable can be accessed anywhere
}

console.log(window.a); //OUTPUT: 20
//variables declared with var belong to window object
```

_NOTE: Variables declared outside the function with both var and let are in global scope but the difference is that **variables declared with var belong to window object** but **variables declared with let do not belong to window object**._

### Local Scope

In JavaScript, we have two types of local scope.

- Function Scope
- Block Scope

#### Function Scope

Whenever we create a new function, a new scope is created. Every function has their own scope. So, when we declare a variable inside a function, we can access that variable within only that function. That variable cannot be accessed outside that function.

```js
let firstName = "Prabesh"; //Global Scope Variable

function displayname() {
  //Local Scope Begins
  let lastName = "Thapa";
  console.log(`${firstName} ${lastName}`);
}
//displayName local scope ends

displayName();

console.log(lastname);
// OUTPUT: ReferenceError: lastName is not defined
```

#### Block Scope

By using **let and const**, we can declare local scope in block statements like **for loop, if statements etc**.

When we declare a variable with **var**, the variable has either global scope or local scope (inside a function). Even if we declare the variable with var inside any block like **for, while, if statement**, the variable is still avaiable throughout the function.

But when we declare the variable with **let or const** within a block, we can access that variable only within that block.

```js
function getGender() {
  let gender = "male";

  if (gender === "male") {
    console.log(`${gender}: Boy`);
    //OUTPUT: male: Boy
  }
  console.log(gender);
  //OUTPUT: ReferenceError: gender is not defined.
}
```

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

<br />

[<-- Previous [JavaScript Engine]](./01-Javascript-Engine.md) <div style="text-align: right;"> [Next [Data Types] -->](03-Data-Types.md)</div>

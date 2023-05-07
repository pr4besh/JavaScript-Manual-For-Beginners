# `this` Keyword

In simple terms, `this` keyword in JavaScript refers to an object upon which a function is invoked. This means that `this` can only be used in a function, or globally.

`this` is used to point to an instance of an object from its own constructor or its method and also to keep track of the execution context (lexical scope) - which is often based on where the function is called from.

```js
function myself() {
  this.name = "Prabesh";
  console.log(this); // OUTPUT: myself {"name": "Prabesh"}
}

let intro = new myself();
```

In the example above, `myself` is used as constructor for the object of type `myself`. Here, `this` reference points to itself i.e. myself {name: "Prabesh"}.

When we use the `new` keyword to create an instance of the `myself()` function, it creates new object and sets `this` to refer to that object. In this case, the `name` property is set to the new object created by the `new` operator.

So, when we create a new instance of `myself()` using `let intro = new myself()`, the `name` property is set on the newly created object, and `this` refers to that object. Therefore, `intro` will refer to an object with a `name` property of "Prabesh".

## `this` in function

When used in either of function or globally, `this` refers to the window object.

```js
function foo() {
  console.log(this);
}

foo(); // OUTPUT : Window
```

Here, when we call the `foo()` function without `new` keyword, `this` refers to the global object (which could be `window` in browser or `global` in Node.js).

However, when we want to use the function as constructor of an object (create an object of type `foo`), `this` keyword changes its context to the instance of `bar` object itself and no longer global object.

```js
function foo() {
  console.log(this);
}

let bar = new foo(); //Output: foo{}
typeof bar; //Ouput: 'object'
```

## `this` in methods

When a function is a method of an object, then `this` refers to object that the method is a member of. This allows us to access and manipulate the properties of the object within the method.

_Example:_

```js
const user = {
  name: "Prabesh",
  age: 23,
  greet: function () {
    console.log(`Hello, my name is ${this.name}`);
  },
};

user.greet(); // Output: "Hello, my name is Prabesh"
```

In the above example, `user` is an object that has a `greet()` method. When we call `user.greet()`, `this` refers to the `user` object. Hence, within the `greet()` method, we can access the `name` property of `user` object using `this.name`.

## `this` in event handlers

The value of `this` inside handler function may not be what we expect it to be. The value of `this` inside an event handler function is determined by how the function is called. In most cases, `this` will refer to DOM element that triggered the event.

For example, if you have a button with an `onClick` attribute that calls a function, the value of `this` inside that function will be the button element. We can use `this` keyword to access properties and methods of the object that the event is asscoiated with. For example, we can use `this.textContent` property to get the text content of the button object.

```php
<button id="myButton">Click me</button>

<script>
function myFunction() {
  console.log(this); // logs the button element
  // Output: <button id="myButton">Click me</button>
}

// Attach the event handler to the button's click event.
document.getElementById("myButton").addEventListener("click", myFunction);
</script>
```

When the button is clicked, the `myClickHandler()` function will be called. The `this` keyword will refer to the button object, so you can use the `this` keyword to access and modify the button's properties and methods.

Now, let's consider annther example:

```js
function cookFood(dish) {
  this.dish = dish;
  this.time = time;

  function setTime(sec) {
    setTimeout(function () {
      console.log(this.dish + " cooked for " + sec + " seconds");
    }, sec * 1000);
  }
}

let curry = new cookFood("Curry"); // this.dish = "Curry"
curry.setTime(3); // Output: undefined cooked for 2 seconds
```

So, what happened here? We have set `this.dish="Curry"` when constructing the `cookFood` object but we get "undefined cooked for 2 seconds" when we expected the output to be "Curry cooked for 2 seconds".

Here, when we call the `setTimeout` function, it creates a nre execution context for the anonymous function that we pass as an argument, which has its own `this` context. Hence, when the anonymous function executes, `this.dish` will be `undefined` because `this` refers to the global object, not the `cookFood` object we created.

This is where arrow functions comes into rescue.

## `this` in arrow functions

Arrow functions help us write more concise and efficient code. Arrow functions does not create it's own execution context but inherits `this` from outside function where the function is defined.

Therefore, the problem in the above code can be fixed just br replacing the regular function for the anonymous function with arrow function.

```js
function cookFood(dish) {
  this.dish = dish;
  this.time = time;

  function setTime(sec) {
    setTimeout(() => {
      console.log(this.dish + " cooked for " + sec + " seconds");
    }, sec * 1000);
  }
}

let curry = new cookFood("Curry"); // this.dish = "Curry"
curry.setTime(3); // Output: Curry cooked for 2 seconds
```

Since, arrow functions do not create their own `this` context. the `this` will refer to the `cookFood` object we created.

# Function Borrowing

Function borrowing is a concept that allows us to reuse the methods of one object on another object. Simply put, we can borrow the methods of one object and use them on other object.

## Implicit Binding

Implicit binding is the default way that `this` is determined in a function call. Whenever we invoke a method of an object using the dot notation, the `this` keyword will point to the object with which it was invoked. In simple terms, when a function is called as a method of an object, `this` is set to the object itself.

```js
const user = {
  name: "John",
  greetUser: function () {
    console.log("Welcome to JavaScript " + this.name);
  },
};

user.greetUser(); // Output: "Welcome to JavaScript John"
```

In this example, `greetUser()` is called as a method of `user`, so `this` is set to `user`.

## Explicit Binding

Explicit binding in JavaScript refers to the technique of manually setting the `this` keyword inisde a function using the `call()`, `apply()` or `bind()` methods. We use explicit binding when we want to access the methods of an object with the values provided by another object.

### 🤝 bind()

The `bind()` method creates and returns a new function, whose `this` keyword is set to object which was passed to it. It _binds_ a method to an object and returns to be invoked later.

```js
function greet() {
  console.log("Welcome " + this.name);
}

const user1 = {
  name: "Prabesh",
};

const user2 = {
  name: "Laxmi",
};

const greetUser1 = greet.bind(user1);
const greetUser2 = greet.bind(user2);

greetUser1(); // Output: "Welcome Prabesh"
greetUser2(); // Output: "Welcome Laxmi"
```

In the above example, we have function `greet()` and objects `user1` and `user2` with `name` properties. We are using the `bind()` method to create two new functions `greetUser1()` and `greetUser2()` which
have their `this` value bound to `user1` and `user2` respectively.

Let's have a look at another example:

```js
const user = {
  firstName: "Super",
  lastName: "Mario",
  greet: function () {
    console.log("Hello, I am " + this.firstName + " " + this.lastName + ".");
  },
};

user.greet(); // Output: "Hello, I am Super Mario."

const user2 = {
  firstName: "Bob",
  lastName: "Builder",
};

const intro = user.greet.bind(user2);
intro(); // Output: Hello, I am Bob Builder.
```

Here, we defined an object call `user` that has three properties: `firstName`, `lastName` and `greet`. The `greet` property is a function that logs a message including `firstName` and `lastName`. When we call `user.greet()`, we are invoking the `greet` function with `this` referring to `user` object. Hence, we get a output of "Hello, I am Super Mario". This concept is referred as `impilicit binding`.

Next, we define another object called `user2` that has two properties: `firstName` and `lastName`. We then create a function called `intro` by using the `bind()` method to bind the `this` keyword of the `greet` function to the `user2` object. This means when we call `intro()` function, `this` inside the `greet` function will refer to the `user2` object and the output will be "Hello, I am Bob Builder."

To summarize, by using `bind()`, we are essentially creating a new function that has its `this` value set to `user2` object. This allows us to resue the `greet` function with a different object. This concept is referred as `explicit binding`.

### 🤙 call()

The `call()` method works similar to `bind()` but has one major difference. As we know, `bind()` method returns a function that can be invoked later but the `call()` method invokes a function and returns the result.

```js
function greet() {
  console.log("Hello, my name is " + this.name);
}

const person = {
  name: "Ninja",
};

greet.call(person); // Output: "Hello, my name is Ninja"
```

Here, we hava a `greet` function and an object `person` with a `name` property. We are using the `call()` method to call `greet()` function with `person` as the context to `this`. As a result, we get an output of "Hello, my name is Ninja".

let us consider another example:

```js
const user = {
  firstName: "Sonic",
  lastName: "Hedgehog",
  greet: function (place) {
    console.log(`I am ${this.firstName} ${this.lastName} from ${place}`);
  },
};

user.greet("Colorado"); // Output: I am Sonic Hedgehog from Colorado

const user2 = {
  firstName: "Ninja",
  lastName: "Turtle",
};

user.greet.call(user2, "Texas"); // Output: I am Ninja Turtle from Texas
```

In this example, we have two objects: `user` and `user2`. We are borrowing the `greet()` function from `user` object using `call()` method abnd binding it with `user2` object.

By using the `call()` method, we are invoking the `greet` function in the context of `user2` object. The first argument to `call()` is the object that `this` should refer to inside the fucntion, and any subsequent arguments are passed as arguments to the function itself.

### 👏 apply()

The `apply()` method is similar to `call()` method, but takes an array of arguments instead of inidividual arguments. In the `call()` method, we can pass multiple parameters, but in `apply()` method, we have to pass in single array that would contain all the parameters.

```js
const user = {
  firstName: "Cristiano",
  lastName: "Ronaldo",
  greet: function (club, country) {
    console.log(
      `I am ${this.firstName} ${this.lastName} from ${country} playing for ${club}.`
    );
  },
};

user.greet("Al-Nassr", "Portugal"); // Output: I am Cristiano Ronaldo from Portugal playing for Al-Nassr.

const user2 = {
  firstName: "Lionel",
  lastName: "Messi",
};

user.greet.apply(user2, ["PSG", "Argentina"]); // Output: I am Lionel Messi from Argentina playing for PSG.
```

By using `apply()`, we're essentially invoking the `greet` function in the context of the `user2` object. The first argument to `apply()` is the object that `this` should refer to inside the function, and the second argument is an array of arguments to pass to the function itself. In this case, we're passing an array of two elements, "PSG" and "Argentina", which are used as the `club` and `country` parameters in the `greet` function, respectively.

**_Summary:_**

- By default, the methods of an object are implicitly bounded to the object itself, and we can access them using the dot (.) operator.
- To access the methods of other objects, we need to explicitly bind them to the object using the `bind()`, `call()`, or `apply()` methods, with each one of them having its own use cases.

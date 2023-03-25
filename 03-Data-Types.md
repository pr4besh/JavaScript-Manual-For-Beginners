**Table of Content**

- [Data Types in JavaScript](#data-types-in-javascript)
  - [Numeric Data Type](#numeric-data-type)
  - [String Data Type](#string-data-type)
  - [Boolean Data Type](#boolean-data-type)
  - [Null Data Type](#null-data-type)
  - [Undefined Data Type](#undefined-data-type)
  - [Symbols Data Type](#symbols-data-type)
- [Objects in JavaScript](#objects-in-javascript)
  - [Create, Read, Update and Delete (CRUD) in Objects](#create-read-update-and-delete-crud-in-objects)
    - [Create](#create)
    - [Read](#read)
    - [Update](#update)
    - [Delete](#delete)
    - [Other Useful Methods to Know](#other-useful-methods-to-know)
  - [Built-In JavaScript Objects](#built-in-javascript-objects)
    - [Array Object](#array-object)
      - [Properties of an Array](#properties-of-an-array)

# Data Types in JavaScript

There are six types of primitive data types we use in JavaScript.

- numeric
- string
- Boolean
- null
- undefined
- symbol (introduced in ES6)

## Numeric Data Type

Numeric data type handles numbers. It can be any numbers including decimal numbers like 3.14.

```js
let number = 1;
let integer = 1.12345;
let negativeNumber = -1;
let negativeInteger = -1.1234;
```

## String Data Type

String data type holds letters and symbols. We wrap our string of texts in quotation marks. We can use either of single('') or double quotation ("") mark. But we need to make sure we start and end with the same quotation. in some case, if we want to include the quotation in our string of texts, we can escape the string quotes by placing a backslash infornt of them.

```js
let quote = "Everybody has a monster";
let mixedQuote = 'This keeps the "Quotation Mark".';
```

## Boolean Data Type

Boolean data type holds the value either true or false. We can store _true/false_ in a variable by typing them without quotation.

```js
var isSingle = true;
```

## Null Data Type

When we want a variable to be empty but not undefined , we set the variable to null (without quotation mark).

```js
let salary = null;
```

## Undefined Data Type

JavaScript is a weakly typed language, therefore the data type for variable are determined only after some value is stored in the variable. So, if no value is stored in a varibale, it is initalized as undefined.

## Symbols Data Type

Symbols data types are the primitive data types introsuces in ECMAScript 2015. Once we create a symbol, its value are kept private and for internal use. All that remains is the symbol reference.

We can create a symbol by simply calling Symbol() function.

```js
const myVariable = Symbol();
```

We get a new and unique symbol everytime we invoke a Symbol function(). Each symbol is guaranteed to be different from other symbols created.

```js
Symbol() === Symbol(); //OUTPUT: false
```

We can also pass parameter to Symbol() function which can be useful for debugging.

```js
console.log(Symbol("Some Test"));
```

We mostly use Symbols to avoid name clashing between object properties sicnce no symbol is equal to other.

```js
const NAME = Symbol();
const person = {
  [NAME]: "Flavio",
};

person[NAME]; //'Flavio'

const RUN = Symbol();
person[RUN] = () => "Person is running";
console.log(person[RUN]());
```

**typeof operator**

If we ever want to know the data type of a certain variable, we can use **typeof** operator.

```js
let name = "Prabesh";
console.log(typeof name); //OUTPUT: String

let isSingle = true;
console.log(typeof isSingle); //OUTPUT: Boolean
```

# Objects in JavaScript

**In JavaScript, EVERYTHING is an Object.**

Objects are the primitibe data structure in JavaScript. We define objects using curly brackets {} and keep key-value pairs seperated by comma.

```js
const myself = {
  firstName: "Prabesh",
  lastName: "Thapa",
  email: "iamprabesh@proton.me",
  nickName: "entry",
};
```

## Create, Read, Update and Delete (CRUD) in Objects

### Create

```js
// Creating an empty object
let player = {};

player.name = "Cristiano Ronaldo";
player["sports"] = "Football"; //Using [] is also valid
player.nickname = "GOAT";
player.country = "Portugal";

console.log(player);

// OUTPUT:
// {
//     "name": "Cristiano Ronaldo",
//     "sports": "Football",
//     "nickname": "GOAT",
//     "country": "Portugal"
// }
```

Or, we can simply add all key-value pairs at oncce.

```js
let player = {
  name: "Cristiano Ronaldo",
  sports: "Football",
  nickname: "GOAT",
  country: "Portugal",
};
```

### Read

We use the `.` operator to access the values of an object.

```js
player.name; //OUTPUT: "Cristiano Ronaldo
player.nickname; //OUTPUT: "GOAT"
```

We can also use the square brackets `[]` to access these properties.

```js
player["sports"]; //OUTPUT: "Football"
player["country"]; //OUTPUT: "Portugal"
```

### Update

We can update the value of a key by overriding the previous value.

```js
player.name = "Cristiano Alveiro Dos Santos Ronaldo";
```

### Delete

We can use the `delete` operator to remove a property from an object.

SYNTAX:

```
delete object.property
delete object[property]
```

```js
const user = {
  firstname: "Entry",
  lastname: "Eemroy",
};

console.log(user.firstname);
// OUTPUT: "Eemroy"

delete user.firstname;

console.log(user.firstname);
// OUTPUT: undefined
```

### Other Useful Methods to Know

**Print Keys from the object**

`Object.keys(player);`

```js
["name", "sports", "nickname", "country"];
```

**Print values from the object**

`Object.values(player);`

```js
["Cristiano Ronaldo", "Football", "GOAT", "Portugal"];
```

## Built-In JavaScript Objects

JavaScript offers four buil-in obejcts: `Array`, `Date`, `Math`, and `String`. All these objects have their own special purpose.

### Array Object

JavaScript Arrays are dynamically created special kind of object. Arrays store a numbers of variables including zero, which are known as empty array. These variables do not necesarily need to have same type. The variables stored in array have no names. These variables are accessed using non-negative integer index value.

If an array has `n` variables, we can say that the length of that array is `n`. These variables are referenced using integer index form `0` to `n-1`.

- Arrays are resizable and can contain mixture of different data types.
- Arrays are zero-indexed i.e. the first element of array is at index `0`.
- Copying arrays creat e a shallow copy, rather than deep copies.

**_A shallow copy of an object is a copy whose properties share the same references (point to the same underlying values) as those of the source object from which the copy was made. As a result, when you change either the source or the copy, you may also cause the other object to change too — and so, you may end up unintentionally causing changes to the source or copy that you don't expect `[mdn]`._**

**_A deep copy of an object is a copy whose properties do not share the same references (point to the same underlying values) as those of the source object from which the copy was made. As a result, when you change either the source or the copy, you can be assured you're not causing the other object to change too; that is, you won't unintentionally be causing changes to the source or copy that you don't expect`[mdn]`._**

#### Properties of an Array

Array object has one property, `length`. the `length` property indicates the number of component stores in that array.

Synatx:

```js
arrayObject.length;
```

Examples:

```js
const arr1 = [1, 2, 3];
const arr2 = new Array(9);
const arr3 = new Array(-10); // Negative numbers are not allowed

console.log(arr1.length); // OUTPUT: 3

console.log(arr2.length); //OUTPUT: 9

console.log(arr3.length); //OUTPUT: RangeError: Invalid array length
```

 <!-- ?TODOS -->
 <!-- Prototypal Inheritance -->
 <!-- Object Protoype -->

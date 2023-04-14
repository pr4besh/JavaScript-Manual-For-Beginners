**Table of Content**

- [Type Casting](#type-casting)
  - [Implicit Type Casting in JavaScript](#implicit-type-casting-in-javascript)
    - [Implicit Type Conversion to Number](#implicit-type-conversion-to-number)
    - [Implicit Type Conversion to String](#implicit-type-conversion-to-string)
  - [Explicit Type Casting](#explicit-type-casting)
    - [Explicit Type Conversion to Number](#explicit-type-conversion-to-number)
    - [Explicit Type Conversion to String](#explicit-type-conversion-to-string)
    - [Explicit Type Conversion to Boolean](#explicit-type-conversion-to-boolean)
  - [Type Conversion vs Type Coercion](#type-conversion-vs-type-coercion)

# Type Casting

JavaScript provides us many data types to work with and although JavaScript is a losely typed language, there will be some cases where we want to change the data types of certain variables. This is called Type Casting. Type Casting sometimes happens automatically or implicitly in our JavaScript engine and sometimes we have to specify that the type casting needs to be performed.

There are two type of type conversions in JavaScript.

- Implicit Conversion: Automatic Type Conversion
- Explicit Conversion: Manual Type COnversion

## Implicit Type Casting in JavaScript

Under certain conditions, JavaScript automatically converts one data type to another. This is known as implicit conversion.

### Implicit Type Conversion to Number

When a string type is used with a number type in mathematical expression using mathematical operators, the string numbers are changed into number type implicitly before performing the operation and then the resulting value is therefore valid number type.

If for some reasons, the implicit numeric conversion is not possible, it results in the vakue being a `NaN` (Not a Number).

Example:

```js
let sum = "10" + "20";
console.log(sum); //OUTPUT: 30
console.log(typeof sum); //OUTPUT: number

let product = "10" * 2;
console.log(product); //OUTPUT: 20
console.log(typeof product); //OUTPUT: number

let remainder = "10" / "divide";
console.log(remainder); //OUTPUT: NaN
```

### Implicit Type Conversion to String

When a string value is aded to the number, that number value is changed into string and the resulting value will be of type string.

```js
let sum = "20" + 23;
console.log(sum); //OUTPUT: 2023
console.log(typeof sum); //OUTPUT: String
```

## Explicit Type Casting

### Explicit Type Conversion to Number

We can use the `Number()` constructor function to change the non-numeric value like boolean or number in string to number data type.

```js
let value = "20";
let result = Number(value);
console.log(reuslt); //OUTPUT: 20
console.log(typeof result); //OUTPUT: number

let value = true;
let result = Number(value);
console.log(reuslt); //OUTPUT: 1
//(true converts to 1 while false converts to 0)
console.log(typeof result); //OUTPUT: number
```

### Explicit Type Conversion to String

We can use the `String()` constructor function to change the non-numeric value like boolean or number in string to String data type.

```js
let value = 20;
let result = String(value);
console.log(reuslt); //OUTPUT: "20"
console.log(typeof result); //OUTPUT: string

let value = false;
let result = String(value);
console.log(reuslt); //OUTPUT: "false"
console.log(typeof result); //OUTPUT: string

let value = 20 + 23;
let result = String(value);
console.log(reuslt); //OUTPUT: '43'
console.log(typeof result); //OUTPUT: string
```

### Explicit Type Conversion to Boolean

In JavaSciript, number 0 relates to false and number 1 relates to true. An empty string `""` relates to false while non-empty strings relate to true. Everything in JavaScript is truthy or falsy.

We can use the `Boolean()` constructor function to convert a number or string into Boolean.

```js
let greet = "Hello";
let result = Boolean(greet);
console.log(result); //OUTPUT: true
console.log(typeof result); //OUTPUT: Boolean

let value = 0;
let result = Boolean(value);
console.log(result); //OUPTUT: false
conole.log(typeof result); //OUTPUT: Boolean
```

## Type Conversion vs Type Coercion

The key difference between type coercion and type conversion is that type conversion is always implicit whereas type conversion can either be implicit or explicit.

[<-- Previous [Data Types]](./03-Data-Types.md) <div style="text-align: right;"> [Next [Data Structure] -->](./05-Data-Structure.md)</div>

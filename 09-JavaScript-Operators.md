**Table of Content**

- [Expression and Operators](#expression-and-operators)
  - [Types of Operator](#types-of-operator)
    - [`Assignment Operator`](#assignment-operator)
    - [`Comparision Operator`](#comparision-operator)
    - [`Arithematic Operator`](#arithematic-operator)
    - [`Logical Operator`](#logical-operator)
      - [`Logical AND (&&)`](#logical-and-)
      - [`Logical OR (||)`](#logical-or-)
      - [`Logical NOT (!)`](#logical-not-)
    - [`Conditional (Ternary) Operator`](#conditional-ternary-operator)
    - [`Unary Operator`](#unary-operator)
    - [`Relational Operator`](#relational-operator)

# Expression and Operators

An expression is a valid piece of code that resolves to a value. There are two types of expressions: those that have effects such as asssigning the value and those who evaluate value.

For example: `x = 7` is a expression that assigns the value of 7 to the variable `x` usig the `=` operator while the expression `2+2` uses the operator `+` to add 2 and 2 together and returns a value of 4.

## Types of Operator

### `Assignment Operator`

It assigns a value to its left operand to the value at its right operand with the operator `=`.

### `Comparision Operator`

It compares its operands and returns a logical value based on whether the comparision is `true` or `false`. If two operands are not of same type, JS attempts to convert them to appropriate type for comparision.

| Operator                   | Description                                                                                         |
| -------------------------- | --------------------------------------------------------------------------------------------------- |
| Equal (==)                 | Returns true if the operands are equal.                                                             |
| Not equal (!=)             | Returns true if the operands are not equal.                                                         |
| Strict equal (===)         | Returns true if the operands are equal and of the same type. See also Object.is and sameness in JS. |
| Strict not equal (!==)     | Returns true if the operands are of the same type but not equal, or are of different type.          |
| Greater than (>)           | Returns true if the left operand is greater than the right operand.                                 |
| Greater than or equal (>=) | Returns true if the left operand is greater than or equal to the right operand.                     |
| Less than (<)              | Returns true if the left operand is less than the right operand.                                    |
| Less than or equal (<=)    | Returns true if the left operand is less than or equal to the right operand.                        |

### `Arithematic Operator`

It takes numerical values as operands and returns single numerical value.The standard arithematic operations are addition `(+)`, subtraction `(-)`, multiplication `(*)` and division `(/)`.

```js
20 / 2; //10
2 + 2; //4
10 * 2; //20
```

In addition to the standard arithematic operations `(+,-,*,/)`, JS also provides other arithematic operators.

| Operator                   | Description                                                                                |
| -------------------------- | ------------------------------------------------------------------------------------------ |
| Equal (==)                 | Returns true if the operands are equal.                                                    |
| Not equal (!=)             | Returns true if the operands are not equal.                                                |
| Strict equal (===)         | Returns true if the operands are equal and of the same type.                               |
| Strict not equal (!==)     | Returns true if the operands are of the same type but not equal, or are of different type. |
| Greater than (>)           | Returns true if the left operand is greater than the right operand.                        |
| Greater than or equal (>=) | Returns true if the left operand is greater than or equal to the right operand.            |
| Less than (<)              | Returns true if the left operand is less than the right operand.                           |
| Less than or equal (<=)    | Returns true if the left operand is less than or equal to the right operand.               |

###` Bitwise Operator`

Bitwise operator treats their operands as a set of 32 bits (1s and 0s). For example, the decimal `7` has a binary represntation of `111`. Bitwise operators perform their operations on such binary representations but they return numerical values.

| Operator              | Description                                                                                      |
| --------------------- | ------------------------------------------------------------------------------------------------ |
| Bitwise AND (`a & b`) | Returns a one in each bit position for which the corresponding bits of both operands are ones.   |
| Bitwise OR (`a \| b`) | Returns a zero in each bit position for which the corresponding bits of both operands are zeros. |
| Bitwise XOR (`a ^ b`) | Returns a zero in each bit position for which the corresponding bits are the same.               |
| Bitwise NOT (`~ a`)   | Inverts the bits of its operand.                                                                 |

### `Logical Operator`

They are typically used with boolean values however `&&` and `||` operators actually return the value of one of the specified operands,so if the operands are used with non-boolean values, they may return non-boolean values.

| Operator            | Description                                                                                                                                                                                                       |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Logical AND `(&&)`  | `(a && b)` returns `a` if it can be converted to false; otherwise, it returns `b`. Thus, when used with Boolean values, `&&` returns `true` if both operands are `true`; otherwise, returns `false`.              |
| Logical OR `(\|\|)` | `(a \|\| b)` returns `a` if it can be converted to true; otherwise, it returns `b`. Thus, when used with Boolean values, `\|\|` returns `true` if either operand is `true`; if both are `false`, returns `false`. |
| Logical NOT `(!)`   | `(!a)` returns `false` if its single operand can be converted to `true`; otherwise, it returns `true`.                                                                                                            |

#### `Logical AND (&&)`

```js
const weirdo = "Cat" && "Dog"; //OUTPUT: Dog
```

Here, `Cat && Dog` evaluates to "Dog" because as mentioned above, `&&` operator when used with two operands, evaluates left operand first and if it can be converted to `false`, it returns the left-hand operand _(Cat in this case)_ else returns the right-hand operand _(Dog in this case)_.

To elaborate, the left-hand operand "Cat" can be converted to `true`, since it is not a empty string. Therefore, JavaScript proceeds to evaluate right-hand operand "Dog" which also can be converted to `true`. _Since, both the operands are `true`, logical AND operator returns the right-hand operator_ i.e. Dog.

**More Examples of `&&` Operator:**

```js
const a1 = true && true; // returns true
const a2 = true && false; // returns false
const a3 = false && true; // returns false
const a4 = false && 3 === 4; // returns false
const a5 = "Cat" && "Dog"; // returns Dog
const a6 = false && "Cat"; // returns false
const a7 = "Cat" && false; // returns false
```

You should try to understand these expressions and the reasons for yourself.

#### `Logical OR (||)`

```js
const nextWeirdo = "Cat" || "Dog"; //OUPUT: Cat
```

Here, `Cat || Dog` evaluates to "Cat" because as mentioned above, `||` operator when used with two operands, evaluates left operand first and if it can be converted to `true`, it returns the left-hand operand _(Cat in this case)_ else returns the right-hand operand _(Dog in this case)_.

To elaborate, the left-hand operand "Cat" can be converted to `true`, since it is not a empty string. Therefore, JavaScript returns the left-hand operand i.e. "Cat". The right-hand operand "Dog" is not even evaluated since the right-hand operand is already `true`.

**More Examples of `||` Operator:**

```js
const o1 = true || true; // returns true
const o2 = false || true; // returns true
const o3 = true || false; // returns true
const o4 = false || 3 === 4; // returns false
const o5 = "Cat" || "Dog"; // returns Cat
const o6 = false || "Cat"; // returns Cat
const o7 = "Cat" || false; // returns Cat
```

#### `Logical NOT (!)`

```js
const n1 = !true; // returns false
const n2 = !false; // returns true
const n3 = !"Cat"; // returns false
```

### `Conditional (Ternary) Operator`

Conditional Operator is the only JavaScript operator that takes three operands.

Syntax:

```
condition ? val1 : val2;
```

If the condition is `true`, the operator has the value of `val1` else it has the value of `val2`. We can use the ternary operator anywhere we would use standard operator.

Example:

```js
const entry = age >= 18 ? "accepted" : "rejected";
```

This statement assigns the value of `entry` to "accepted" if the age is 18 or more else it assigns the value to "rejected".

### `Unary Operator`

A unary operation is an operation with only one operand.

- `delete`: it deletes and object's property.

```
delete object.property;
delete object[propertyKey];
delete objectName[index];
```

If the `delete` operator succeeds, it removes the property from the object. When we try to access that property afterwards, it will return `undefined`.

```js
delete Math.PI; // returns false (cannot delete non-configurable properties)

const myObj = { x: 2 };
delete myObj.h; // returns true (can delete user-defined properties)
```

- `typeof`: This operator returns a string indicating the type of the operand.

```js
const addFunc = new Function("2 + 2");
const shape = "round";
const size = 12;
const fruits = ["Apple", "Mango", "Orange"];
const today = new Date();
const isSingle = true;

typeof addFunc; // returns "function"
typeof shape; // returns "string"
typeof size; // returns "number"
typeof fruits; // returns "object"
typeof today; // returns "object"
typeof doesntExist; // returns "undefined"
typeof isSingle; // returns "boolean"
```

### `Relational Operator`

A relational operator compares its operands and returns a value based on whether the comparison is truthy.

- `in`: This operator returns `true` if the specified property is in the specified object.

Syntax:

```
propertyName in objectName;
```

```js
// Arrays
const fruits = ["mango", "apple", "grape", "plum", "papaya"];
0 in fruits; // returns true
3 in fruits; // returns true
6 in fruits; // returns false
"apple" in fruits; // returns false
// (you must specify the index number, not the value at that index)
"length" in fruits; // returns true (length is an Array property)

// built-in objects
"PI" in Math; // returns true
const myName = new String("entry");
"length" in myString; // returns true

// Custom objects
const myFriends = { name: "Yogendra", hobby: "Sleeping", year: 2000 };
"name" in myFriends; // returns true
"hobby" in myFriends; // returns true
```

```
Well, you may be wondering why `0 in fruits` evaluates to `true` but `apple in fruits` evaluate to `false`.
```

The reason for this is because the `in` operator in JavaScript is used to check if a specified property/key exists in an `object` or `array`.

In the case of `0 in fruits`, it is checking whether the fruits array has a property/key of 0, which it does since arrays in JavaScript are objects with numeric keys starting from 0. Therefore, the expression 0 in fruits returns `true`.

However, "apple" in fruits is checking whether the fruits array has a property/key of "apple", which it does not, since the elements of the array are not considered keys. Therefore, the expression "apple" in fruits returns `false`.

To check if a value exists in an array, you can use the `includes()` method instead: `fruits.includes("apple")` would return `true` because the value "apple" exists in the array.

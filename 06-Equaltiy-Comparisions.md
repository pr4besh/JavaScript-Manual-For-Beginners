**Table of Content**

- [Value Comparison Operators](#value-comparison-operators)
  - [Comparing Objects in JavaScript](#comparing-objects-in-javascript)
    - [Referential Equality](#referential-equality)
    - [Manual Comparision](#manual-comparision)
    - [Shallow Equality](#shallow-equality)
    - [Deep Equality](#deep-equality)

# Value Comparison Operators

When we have to compare two values in JavaScript, we use comparison operators provided by default in JavaScript. When we compare twovalues, a `boolean (true or false)` value is returned.

There are eight comparision operators in JavaScript.

- `>` : greater than - Returns `true` if the operand on the left is greater than on the right of the operand.

```js
let result = 40 > 60;
console.log(result); //OUTPUT: false
```

- `<` : less than - Returns `true` is the operand on the left is less than the operand on the right.

```js
let result = 40 < 60;
console.log(result); //OUTPUT: true
```

- `>=` : greater than or equal to - Returns `true` if the oeprand on the left is greater or equal to the operand on right.

```js
let result1 = 20 >= 10;
let result2 = 10 >= 10;

console.log(result1); //OUTPUT: true
cosnole.log(result2); //OUTPUT: true
```

- `<=` : less than or equal to - Returns `true` if the operand on the left is less than or equal to the operand on the right.

```js
let result = 40 <= 60;
console.log(result); //OUTPUT: true
```

- `==` : equal to - Returns `true` if the operand on the left is equal to the operand on the right.

```js
let result = 4 == "4";
console.log(result); //OUTPUT: true
```

`==` operators converts both of our values into a common data type and returns true if both operands are equal in value.

- `===` : strictly equal to - returns `true` if the operand on the left is strictly equal to the operand on the right.

```js
let result = 4 === "4";
console.log(result); //OUTPUT: false
```

`===` operators do not convert the operands into same data type and hence only returns `true` id both the operands are equal in values and also of same data type.

- `!=` : not equal to - returns `true` if the operand on the left is not equal to the operand on the right.

```js
let result = 4 != "4";
console.log(result); //OUTPUT: false
```

- `!==` : strict not equal to - returns `true` if the operand on the left is strictly not equal to the operand on the right.

```js
let result = 4 !== "4";
console.log(result); //OUTPUT: true
```

**Equal Operator (==) vs Strict Equal Operator (===)**

| Equal Operator (==)                                                                           | Strict Equal Operator (===)                                                                           |
| --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Converts the operands to same data type before comparision.                                   | Does not convert the operands to same data type before comparison.                                    |
| Returns `true` if both values are equal irrespective of their data type.                      | Returns `true` only if both the values and the data type of the operands are same.                    |
| Example: As `undefined` and `null` are losely equal, `undefined` == `null` returns as `true`. | Example: As `undefined` and `null` are strictly not equal, `undefined` === `null` returns as `false`. |

## Comparing Objects in JavaScript

Comparing Object in JavaScript is difficult than comparing primitive data types since objects are structured data. JavaScript essentially provides us three ways to compare values:

- Strict Equality Operator (===)
- Loose Equality Operator (==)
- `Object.is()` function

### Referential Equality

When we compare objects using any of the above operator, it only returns `true` if the comapred value refers to the same object instance. This is called `referential equality`.

```js
const hero1 = {
  name: "Spider Man",
};

const hero2 = {
  name: "Spider Man",
};

console.log(hero1 === hero1); // OUTPUT: true
console.log(hero1 === hero2); // OUTPUT: false

console.log(hero1 == hero1); // OUTPUT: true
console.log(hero1 == hero2); // OUTPUT: false

console.log(Object.is(hero1, hero1)); // OUTPUT: true
console.log(Object.is(hero1, hero2)); // OUTPUT: false
```

Here, `hero1 === hero1` evaluates to `true` because both operands points to the same object instance `hero1` however `hero1 === hero2`returns `false` because `hero1` and `hero2` are two different object instances although both objects have the same property `name` with the same value of `Spider Man`.

Hence, `Referential Equality` is used when we want to compare the object references, rather than their content (property and value).

### Manual Comparision

We can compare the contents in the object simply by accessing the properties and comparing them manually.

```js
function isUserSame(obj1, obj2) {
    return obj1.fullName === obj2.fullName;
}

const user1 = {
    fullName: "Prabesh Thapa";
}

const user2 = {
    fullName: "Prabesh Thapa";
}

const user1 = {
    fullName: "Laxmi Thapa";
}

console.log(isUserSame(user1, user2)); //OUTPUT: true
console.log(isUserSame(user1, user3)); //OUTPUT: false
```

Manual comparision is the best possible way to to compare the properties of simple objects but it isn't convenient when we have to deal with bigger objects. This is where we can use `Shallow Equality`.

### Shallow Equality

We can get the list of properties in both the objects using the `Object.keys()` method and later check the properties values for equality.

```js
function isUserSame(obj1, obj2) {
  const keys1 = Object.keys(obj1);
  const keys2 = Object.keys(obj2);

  console.log(keys1); //OUTPUT: ["firstName", "lastName", "age"]
  console.log(keys2); //OUTPUT: ["firstName", "lastName", "age"]

  if (keys1.length !== keys2.length) {
    return false;
  }

  for (let key of keys1) {
    if (obj1[key] !== obj2[key]) {
      return false;
    }
  }
  return true;
}

const user1 = {
  firstName: "Prabesh",
  lastName: "Thapa",
  age: 23,
};

const user2 = {
  firstName: "Prabesh",
  lastName: "Thapa",
  age: 23,
};

const user3 = {
  firstName: "Laxmi",
  lastName: "Thapa",
  age: 21,
};

console.log(isUserSame(user1, user2)); //OUTPUT: true
console.log(isUserSame(user1, user3)); //OUTPUT: false
```

Inside the function, `keys1` and `keys2` are arrays containg the property names of `obj1` and `obj2`. Here, `isUserSame(user1, user2)` returns `true` because both `user1` and `user2` have the same properties with same values.

**Shallow Equality doesn't work so well with nested objects however.**

```js
const user1 = {
  firstName: "Prabesh",
  lastName: "Thapa",
  age: 23,
  address: {
    city: "Pokhara",
  },
};

const user2 = {
  firstName: "Prabesh",
  lastName: "Thapa",
  age: 23,
  address: {
    city: "Pokhara",
  },
};

console.log(isUserSame(user1, user2)); //OUTPUT: false
```

Interestingly, although `user1` and `user2` both have same properties and values, shallow equality returns `false`. This is because, the nested object `user1.address` and `user2.address` are different object instances, hence shallow equality considers them to be not equal.

This problem can fortunately be solved with `Deep Equality`.

### Deep Equality

Deep equality is similar to shallow equality but with one major difference. During the comparision, a recursive check is performed on the nested objects.

```js
function deepEqual(obj1, obj2) {
  const keys1 = Object.keys(obj1);
  const keys2 = Object.keys(obj2);

  if (keys1.length !== keys2.length) return false;

  for (const key of keys1) {
    const val1 = obj1[key];
    const val2 = obj2[key];
    const areObjects = isObject(val1) && isObject(val2);

    if (
      (areObjects && !deepEqual(val1, val2)) ||
      (!areObjects && val1 !== val2)
    ) {
      return false;
    }
  }
  return true;
}

function isObject(obj) {
  return (obj != null) & (typeof obj === "object");
}
```

The `isObject` function checks if an object is not `null` or `undefined`, and if its type is `object`, returning a boolean value accordingly.

The `deepEqual` function takes two objects as input and recursively compares their properties and values to determine if they are deeply equal (i.e., if they have the same properties with the same values).

To do this, it first gets an array of the keys of each object using `Object.keys()`. If the length of these arrays is not the same, the function immediately returns false.

Then, for each key in the `keys1` array, the function gets the corresponding values from both objects (val1 and val2) and checks if they are both objects using the `isObject` function. If they are, the function recursively calls `deepEqual` on these nested objects to determine if they are equal. If they are not both objects, the function checks if their values are equal using the `!==` operator.

If any of the comparisons in the for loop fail, the function immediately returns false. If all of the comparisons pass, the function returns true.

```js
const user1 = {
  firstName: "Prabesh",
  lastName: "Thapa",
  age: 23,
  address: {
    city: "Pokhara",
  },
};

const user2 = {
  firstName: "Prabesh",
  lastName: "Thapa",
  age: 23,
  address: {
    city: "Pokhara",
  },
};

console.log(deepEqual(user1, user2)); //OUTPUT: true
```

Here, deep equality function correctly determines that both `user1` and `user2` have same properties and values, including the nested objects.

**Summary:**

- Referential equality using `==`, `===` and `Object.is()` checks whether the operands are the instance of same object.
- We can also manually compare the values of properties in the object by accessing the properties of those objects.
- We use shallow equality when the objects to be compared have a lot of properties or if the object is determined at the runtime.
- We use deep equality check if the compared objects have nested objects.

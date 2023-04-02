**Table of Content**

- [Data Structure in JavaScript](#data-structure-in-javascript)
  - [Indexed Collection](#indexed-collection)
    - [Array Object](#array-object)
      - [Properties of an Array](#properties-of-an-array)
      - [Adding element to an Array](#adding-element-to-an-array)
      - [Array Methods](#array-methods)
    - [TypedArray Object](#typedarray-object)
  - [Keyed Collections](#keyed-collections)
    - [Map](#map)

# Data Structure in JavaScript

Groups of data in different forms are one of the fundamental data structures in most of the programming languages. _Normally, groups of data expressed through different data types are known as `Collection`._

The three main Collection groups in JavaScript are -

- Indexed Collections
- Keyed Collections
- DOM Collections

## Indexed Collection

Indexed collection is the colletion of data which is listed by their index. JavaScript collection indicies are _0-based_, meaning they start at index 0 and go up to `n-1`, where `n` is the number of objects in the collection. JavaScript offers two kinds of indexed collections - `Arrays` and `Typed Arrays`.

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

#### Adding element to an Array

We can add an element to an Array by accessing an element through it's index and assign a value to it.

```js
let friends = new Array(5);

friends[0] = "Suman";
friends[1] = "Anil";
friends[2] = "Yogendra";
friends[3] = "Bipin";
friends[4] = "Shusan";

console.log(friends);
//OUTPUT: ["Suman", "Anil", "Yogendra", "Bipin", "Shusan"]
```

In the above example, we have allocated 5 spaces for the array but we still can shrink or expand the size at any tine since the size ais dynamically allocated.

```js
friends[5] = "Laxmi";
friends[6] = "Sumi";

console.log(friends);
// OUTPUT: ["Suman", "Anil", "Yogendra", "Bipin", "Shusan", "Laxmi", "Sumi"]
```

#### Array Methods

Here, we will have a look at the nmost commonly used methods:

- `push()` - Adds an element at the end of an array

```js
let even = [2, 4, 6, 8];
even.push(10);

console.log(even); //OUTPUT: [2,4,6,8,10]
```

- `pop()` - removes the last element of an array

```js
let even = [2, 4, 6, 8];
even.pop();
console.log(even); //OUTPUT: [2,5,6]
```

- `concat()` - joins arrays (two or more) into a single array

```js
//Concat 2 Arrays
let even = [2, 4, 6, 8];
let odd = [1, 3, 5, 7, 9];

let array1 = odd.concat(even);
console.log(array1);
//OUTPUT: [1,3,5,7,2,4,6,8];

//Concat 3 Arrays
let doubles = [10, 11, 12, 13];
let array2 = even.concat(odd, doubles);
console.log(array2);
//OUTPUT: [2,4,6,8,1,3,5,7,9,10,11,12,13]
```

- `join()` - creates and returns a new string by conctenating all the elements in an array seperated by commas `(,)` or **user-specified seperator**.

```js
const life = ["Live", "Laugh", "Love"];

console.log(life.join());
// OUTPUT: "Live,Laugh,Love"

console.log(life.join(""));
// OUTPUT: "LiveLaughLove"

console.log(life.join("-"));
// OUTPUT: "Live-Laugh-Love"
```

- `reverse()` - Just as the name suggests, it reverses the order of elements in an array.

```js
let even = [2, 4, 6, 8, 10];
let reversed = even.reverse();
console.log(reversed);
// OUTPUT: [10,8,6,4,2]
```

- `slice(start, end)` - It returns a shallow copy of portion of an array into an new array from specified `start` to `end` where `end` is not included. **The original array is not modified.**

```js
const hobbies = ["cricket", "football", "anime", "bikinig", "hiking"];

console.log(hobbies.slice(2));
//OUTPUT: ["anime", "bikinig", "hiking"]
console.log(hobbies.slice(2, 4));
//OUTPUT: ["anime", "bikinig"]
console.log(hobbies.slice(1, 5));
//OUTPUT: ["football", "anime", "bikinig", "hiking"]
console.log(hobbies.slice(-3));
//OUTPUT: ["anime", "bikinig", "hiking"]
console.log(hobbies.slice(2, -1));
//OUTPUT: ["anime", "bikinig"]
console.log(hobbies.slice());
//OUTPUT: ["cricket", "football", "anime", "bikinig", "hiking"]
```

### TypedArray Object

`Array` object can be used to store different types of elements in one array and also offers various powerful methods to manipulate the elements in the array.

However, when we need to work with raw binary data, we need to use the `TypedArray` Object. Raw data is processed when manipulating audio and video for example.

JavaScript typed arrays are array-like objects that provide a mechanism for reading and writing raw binary data in memory buffers. JavaScript typed arrays are divided into _`Buffers`_ and _`Views`_.

- Buffer - An object representing a chunk of data implemented by the `ArrayBuffer` object. It is used to represent a fixed-length binary data buffer. To represent this buffer, we create a view - `DataView` and use it to read and write the contents of the buffer. There are various types of views which represent the most common numeric types -
  - `Int8Array`: 8-bit two's complement signed integer
  - `Uint8Array` - 8-bit unsigned integer
  - `Uint8ClampedArray`: 8-bit unsigned integer
  - `Int16Array`: 16-bit two's complement signed array
  - `Uint16Array`: 16-bit unsigned array
  - `Int32Array`: 32-bit two's complement unsigned array
  - `Uint32Array` : 32-bit unsigned array
  - `Float32Array`: 32-bit IEEE floating point number (7 significant digits)
  - `Float64Array`: 64-bit IEEE floating point number (16-bit significant digits)
  - `BigInt64Array`: 64-bit two's complement signed integer
  - `BigUint64Array`: 64-bit unsigned integer

## Keyed Collections

A keyed collection is a collection of data represented in **key-value** notation. These values are acccessed and manipulated with their respective keys. We have two kinds of keyed collection in JavaScript: `Map` and `Set`.

### Map

Map object is the collection of key-value pairs. Keys are always unique in Map meaning, a key in a Map object can only appear once.

**Creating a Map Object**

Suppose, we have a list of `user` object as below:

```js
let virat = { fullName: "Virat Kohli" },
  smith = { fullName: "Steve Smith" },
  root = { fullName: "Joe Root" };
```

Assuming we have to create a map of these players and their country, we can code as below:

```js
let fabThree = new Map();

console.log(typeof fabThree); // OUTPUT: object
console.log(fabThree instanceof Map); // OUTPUT: true
```

The `fabThree` is an instance of `Map` object and it's type is an object as shown above.

**Adding elements to Map**

To assign country to these players, we can use the `set()` method.

```js
fabThree.set(virat, "India").set(smith, "Australia").set(root, "England");
```

The `set()` method maps each players with their specified country.

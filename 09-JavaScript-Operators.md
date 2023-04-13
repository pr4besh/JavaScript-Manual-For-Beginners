# Expression and Operators

An expression is a valid piece of code that resolves to a value. There are two types of expressions: those that have effects such as asssigning the value and those who evaluate value.

For example: `x = 7` is a expression that assigns the value of 7 to the variable `x` usig the `=` operator while the expression `2+2` uses the operator `+` to add 2 and 2 together and returns a value of 4.

## Types of Operator

- Assignment Operator: It assigns a value to its left operand to the value at its right operand with the operator `=`.
- Comparision Operator: It compares its operands and returns a logical value based on whether the comparision is `true` or `false`. If two operands are not of same type, JS attempts to convert them to appropriate type for comparision.

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

- Arithematic Operator: It takes numerical values as operands and returns single numerical value.The standard arithematic operations are addition `(+)`, subtraction `(-)`, multiplication `(*)` and division `(/)`.

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

- Bitwise Operator: Bitwise operator treats their operands as a set of 32 bits (1s and 0s). For example, the decimal `7` has a binary represntation of `111`. Bitwise operators perform their operations on such binary representations but they return numerical values.

| Operator              | Description                                                                                      |
| --------------------- | ------------------------------------------------------------------------------------------------ |
| Bitwise AND (`a & b`) | Returns a one in each bit position for which the corresponding bits of both operands are ones.   |
| Bitwise OR (`a \| b`) | Returns a zero in each bit position for which the corresponding bits of both operands are zeros. |
| Bitwise XOR (`a ^ b`) | Returns a zero in each bit position for which the corresponding bits are the same.               |
| Bitwise NOT (`~ a`)   | Inverts the bits of its operand.                                                                 |

- Logical Operator: They are typically used with boolean values however `&&` and `||` operators actually return the value of one of the specified operands,so if the operands are used with non-boolean values, they may return non-boolean values.

# Conditional Statement

Conditional Statements control behavior in JavaScript and determine weather certain code blocks can run or not. There are different conditional statements in JavaScript such as -

- `if` statement: if a condition is `true`, it is used to run a certain block of code.
- `else` statement: if a condition is `false`, it is used to run a certain block of code.
- `else if` statement: runs a certain block of code if the previous condition is `false`.

## `if` statement

This is the most common type of conditional used and the code below if statement runs only if the specified condition in parentheses `()` is `true`.

```js
if (2 < 5) {
  var result = "This is inside if block";
}

console.log(result); //OUTPUT: "This is inside if block"
```

The condition in the `if-statement` (2 < 5) evaluates to `true` since 2 is less than 5. After the condition is wevaluated to `true`, the code inside the block is run which assigns the value of `result` as "This is inside if block".

## `else` statement

We can add an `else` statement after the `if` statement. We can add an extra block of code to run if the condition does not evaluates as `true`.

```js
if (2 > 5) {
  var result = "This is inside if block";
} else {
  var result = "This is inside else block";
}

console.log(result); //OUTPUT: "This is inside else block"
```

## `else-if` statement

We can also add an `else-if` statement to our `if` statement which adds another condition and it's own code block. We can use multiple `else-if` condition but we have to keep in mind that only the first `else-if` code block is run if the condition is truthy while other remaining `else-if` statements are skipped.

```js
if (2 > 5) {
  var result = "This is inside if block";
else if (2 === 2) {
  var result = "This is inside else-if block";
}
} else {
  var result = "This is inside else block";
}

console.log(result); //OUTPUT: "This is inside else-if block"
```

## switch

We can replace our `if-statements` with `switch` when we wncounter multiple checks. `switch` gives us more descriptive and concise ways to compare a value. We can have one or more `case` blocks and optional `default`.

The value (expression) in the parentheses is strictly compared (===) with the value from the first case (value1 in this case) then to the second case and so on until the condition evaluates to `true`. If the equality is encountered, the code from the corresponding case is executed until the nearest `break` is found. If no case is matched, then the `default` code is executed (if it exists).

_Syntax:_

```js
switch (expression) {
  case value1: // if (expression === value1)
    statements;
  case value2: // if (expression === value2)
    statements;
  case value3: // if (expression === value3)
    statements;
  default:
    statements;
}
```

```js
let goat = "Ronaldo";

switch (goat) {
  case "Messi":
    console.log("Almost");
    break;
  case "Pele":
    console.log("Legend");
    break;
  case "Ronaldo":
    console.log("GOAT");
    break;
  case "Maradona":
    console.log("Magnifico");
    break;
  default:
    console.log("It's your opinion.");
}
```

_Example 2:_

```js
switch (browser) {
  case "Edge":
    alert("You've got the Edge!");
    break;

  case "Chrome":
  case "Firefox":
  case "Safari":
  case "Opera":
    alert("Okay we support these browsers too");
    break;

  default:
    alert("We hope that this page looks ok!");
}
```

# Exception Handling

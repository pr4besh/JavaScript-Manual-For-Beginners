**Table of Content**

- [Loops and Iteration](#loops-and-iteration)
  - [`while` Loops](#while-loops)
  - [`do-while` loop](#do-while-loop)
  - [`for` loops](#for-loops)
  - [`for...of` loop](#forof-loop)
  - [`for...in` loop](#forin-loop)
  - [Controlling Loops](#controlling-loops)

# Loops and Iteration

We regularly face conditions when we need to run our code over and over again until some condition is met. JavaScript provides us several forms to achive this condition.

## `while` Loops

A `while` loop uses the `while` keyword followed by a conditional expression in parentheses `()` and a code block. The loop executes the code block again and again as long as the conditional expression remains truthy. The loop only stops when the condition is met and conditional expression becomes falsy. Else, the loop becomes `infinite` and never stops repeating.

```js
let counter = 1;
while (counter <= 10) {
  console.log(counter);
  counter++; //counter = counter + 1;
}
```

During the execution of `while` loop, JavaScript evaluates the conditional expression inside the parentheses `counter <= 10`. Since, the initial value of the `counter` is 1, the condition evaluates to `true` and hence the JS engine runs the loop's code block. Inside the block, we output the value of counter and increase it's value by 1.

After the first block iteration, JavaScript re-evaluates the conditional expression and sees that the counter value is increased by 1 i.e. 2 which still satisfies the condition and hence again output the counter value and increse by 1. This iteration countinues till the condition is no longer truthy i.e. the value of counter becomes greater than 10. When counter value exceeds 10, the loop stops.

**Looping over Arrays with `while` loop**

```js
let players = ["Ronaldo", "Messi", "Pele", "Maradona", "Zidane"];
let upperCase = [];
let idx = 0;

while (idx < players.length) {
  let convertToUpperCase = players[idx].toUpperCase();
  upperCase.push(convertToUpperCase);
  idx += 1; //idx = idx + 1;
}

console.log(upperCase); //OUTPUT: ["RONALDO","MESSI","PELE","MARADONA","ZIDANE"]
```

## `do-while` loop

The major difference between `while` loop and `do-while` loop is that the `do-while` loop always executes the code in the block at least once while a `while` loop is not certain to do so since the initial condition may be falsy.

In a `do-while` loop, the condition is evaluated at last instead of the begining which allows the code block to run at least once even when the initial condition is falsy.

```js
let input;
do {
  input = prompt("Would you like to play the game again? (y/n)");
} while (input === "y");
```

When the above code is run, weget a prompt `Would you like to play the game again? (y/n)` and if we enter the lowercase `y`, we get the prompt again as long as we enter `y` but once we enter anything other than the letter `y`, the loop stops.

## `for` loops

`for` loops works the same way as `while` loop but with a more strethched and complex syntax.A `for` loop combines variable initialization, loop condition, and the increment/decrement expression in one single line.

_Syntax_

```
for (initialization; condition; increment) {
    //loop code block
}
```

```js
let players = ["Ronaldo", "Messi", "Pele", "Maradona", "Zidane"];
let upperCase = [];

for (let idx = 0; idx < players.length; idx++) {
  let convertToUpperCase = players[idx].toUpperCase();
  upperCase.push(convertToUpperCase);
}

console.log(upperCase); //OUTPUT: ["RONALDO","MESSI","PELE","MARADONA","ZIDANE"]
```

Steps involved:

1. Declare and initialize the `idx` variable to 0.
2. If `idx` is not less than length of array, go to step 6.
3. If `idx` is less than length of array, execute the loop code.
4. Increment `idx`.
5. Go back to Step 2.
6. Output the results.

## `for...of` loop

We can use `for...of` statement to loop over an iterable object such as Array, String, Map, Set etc.

_Syntax:_

```
for (variable of iterable) {
    statement;
}
```

```js
let odd = [1, 3, 5, 7, 9];

for (const num of odd) {
  console.log(num);
}

/* OUTPUT:
1
3
5
7
9
*/
```

## `for...in` loop

The `for...in` loop is used to loop through an object's properties.

_Syntax:_

```
for (variable in object) {
    statement;
}
```

```js
const vars = { x: 2, y: 4, z: 6 };

for (const num in vars) {
  console.log(`${num}: ${vars[num]}`);
}

/*OUTPUT:
"x: 2"
"y: 4"
"z: 6"
*/
```

## Controlling Loops

We can have more control over loops with the keywords `continue` and `break` provided by JavaScript.

- `continue` lets us start a new iteration.

```js
let players = ["Ronaldo", "Messi", "Pele", "Maradona", "Zidane"];
let upperCase = [];

for (let idx = 0; idx < players.length; idx++) {
  if (players[idx] === "Pele") {
    continue;
  }

  let convertToUpperCase = players[idx].toUpperCase();
  upperCase.push(convertToUpperCase);
}

console.log(upperCase); //OUTPUT: ["RONALDO","MESSI","MARADONA","ZIDANE"]
```

As we can see, the `upperCase` array no longer has 'PELE'. That is because when the loop encounters the `continue` keyword, it skips rest of the code and starts a new iteration.

- `break` lets us terminate a loop before condition is met.

There might be some cases when we want to skip the remaining iteration of loops. For example, when we are searching for an certain element in an array, we probably would want to stop the iteration once we find it.

```js
let even = [2, 4, 6, 8, 10, 12, 14];
let indexOfSix = -1;

for (let i = 0; i < even.length; i += 1) {
  if (even[i] === 6) {
    indexOfSix = i;
    break;
  }
}

console.log(indexOfSix);
```

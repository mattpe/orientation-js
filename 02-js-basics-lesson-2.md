# Orientation Course - Basics of JavaScript Programming 2

MP 9/2020

## JavaScript basics, lesson 2

1. Lesson 1 tasks (example solutions & recap)
2. New stuff: Arrays, loops & iteration, scoping, some built-in functions, functions??

---

### Control structure: Basic loops

- [Loops and iteration in MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)
- Loops are a quick and easy way to do something repeatedly

For example, this would be just stupid and looks ugly:

```js
// Counting to ten
console.log('1');
console.log('2');
console.log('3');
console.log('4');
console.log('5');
console.log('6');
console.log('7');
console.log('8');
console.log('9');
console.log('10');
```

and what about if you don't know how many times you need to repeat some operation when coding the application?

this looks more like a work of a software developer:

```js
// Counting to ten
for (let i=1; i<=10; i++) {
  console.log(i);
}
```

#### for loop

[`for` statement in MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)

- `for(init; condition; step) { ... }` - four-part loop construct: initialization;
condition; step, and body

```js
for (let i = 0; i < 3; i++) {
  alert(i);
}


const retirementAge = 65;
for (let age = 0; age <= 100; age += 10) {
  console.log(`${name} is ${age} years old.`);
  if (age >= retirementAge) {
    break; // break statement _can_ be used to jump immediately out from the loop
  }
}
```

#### while loops

[`while` statement in MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/while)

- `while(condition) { ... }` - keep executing body while condition is true

```js

let age = -10;
while (age <= 100) {
  if (age > 65) {
    console.log(`${name}, age ${age} should retire.`);
  } else if (age >= 18) {
    console.log(`${name}, age ${age} is adult.`);
  } else if (age >= 0) {
    console.log(`${name}, age ${age} is not adult at all.`);
  } else {
    console.log(`${name}, age ${age} has a weird age.`);
  }
  age += 10;
}
```

#### do - while loop

- `do { ... } while(condition)` - keep executing body while condition is true, note that condition is evaluated first time only after executing body once

```js
let age = 101;
do {
  console.log(`${name} is ${age} years old.`);
  age++;
} while (age <= 100);
```

#### break and continue

- `break` -> jump out from the loop (next line of code after loop)
- `continue` -> skips the rest of the loop's code block and execution jumps in the first line of the loop

```js
for (let i=0;i<=6;i++) {
  if (i==3) {
    break;
  }
  console.log("The number is " + i);
}

for (let i=0;i<=6;i++) {
  if (i==3) {
    continue;
  }
  console.log("The number is " + i);
}

```

---

### Scoping

- Scope: rules for deciding what names/variables are visible in program execution
- Lexical scoping: visibility is defined by the location of definitions in the program
code
- Global scope: variable is declared outside any code block (scope) -> visible anywhere in the program code
- Local scope: variable is declared inside a code block. In javascript `let` and `const` bindings have a local scope. Old school `var` behaves in different manner. _Just don't use it._
- code blocks are defined with curly braces `{` and `}` and can be recursive
- all code blocks defined within loops, conditional statements (like `if...else`) and functions follow these rules -> most common use of scopes
- use always consistent indentation for readability (code editor's 'format code' functionality helps)

```js
// Global scope, values visible everywhere
const a = 6;
let b = 3;

// Code block
{
  const a = 9; // New variable declaration -> different than global variable 'a'
  const c = 4;
  // A code block inside another code block has it's own scope
  {
    let c = 1; // New variable declaration -> different than outside scope variable 'c'
    console.log(a + b + c); // --> 13
    b = 2; // Global variable
  }
  console.log(a + b); // --> 11
}
console.log(a + b); // --> 8
```

---

### Arrays

[`Array` in MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

- An array allows for storing together related values using an integer index for identification.
- In Javascript arrays are dynamic, ie. they can grow in shrink in size during program execution.
- An array in Javascript is also an object. It is possible to add/remove attributes to/from an array. The indexes in an array are technically property names, however a special syntax (which is familiar from other programming languages) must be used.

```js
> let myGrades = [ 3, 3, 4, 1, 5, 5 ];
undefined
> myGrades;
[ 3, 3, 4, 1, 5, 5 ]
> myGrades[0];
3
> myGrades[2];
4
> myGrades[6];
undefined
> myGrades.length;
6
> myGrades[2] = 3;
3
> myGrades;
[ 3, 3, 3, 1, 5, 5 ]
> myGrades[6] = 4;
4
> myGrades;
[ 3, 3, 3, 1, 5, 5, 4 ]
> myGrades.push(5);
8
> myGrades;
[ 3, 3, 3, 1, 5, 5, 4, 5 ]
> myGrades.pop();
5
> myGrades;
[ 3, 3, 3, 1, 5, 5, 4 ]
```

### Iterating an array with for loops

- using old-school for:

```js
const myStringArray = ["Hello", "World"];
for (let i = 0; i < myStringArray.lengthh; i++) {
    console.log(myStringArray[i]);
}
```

- [for-of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of) is a new loop in ES6 that replaces both for-in and forEach() and supports the new iteration protocol.

```js
let myGrades = [3, 3, 4, 1, 5, 5];
let topGradeCount = 0;
for (const grade of myGrades) {
  if (grade > 4) {
    topGradeCount++;
  }
}
// topGradeCount: 2
```

---

### Functions

- a function contains code that will be executed by an event or by a call to the function.
- syntax:

    ```js
    function functionName(parameter1, param2, ... , paramX) {
       // some code statements
       // use the parameter variable values here (if exists)
    }
    ```

- parameters can be numbers, strings, booleans, arrays, other functions, objects, etc.
- functions that are going to return a value must use the return statement.
- a function can be used to give a name to a snippet of code to clarify its meaning. Functions can also be used to avoid repeating code multiple times. They serve as building blocks out of which whole applications can be constructed.

A function can be defined with keyword function and a name. The argument(s)/parameter(s) of the function are optional and listed in parenthesis after keyword function. The value of the expression after return statement defines the value returned by function when it is called.

```js
function showMessage() {
  alert( 'Hello everyone!');
}
showMessage();


function showMessage(from, text) {
  console.log(from + ': ' + text);
}
showMessage('Carl', 'Important message!');


function calculateSum(a, b) {
  return a + b;
}
let result = calculateSum(1, 2);
console.log(result); // 3


function square(x) {
  return x * x;
}
console.log(square(0)); // 0
console.log(square(3)); // 9
console.log(square(2 - 4)); // 4
console.log(square('five')); // NaN
```

#### Built-in functions

There is a lot of built-in functions (or methods) for different purposes in JS, some examples:

- [Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)
  - Math.random() returns a random number between 0 (inclusive), and 1 (exclusive), e.g: `Math.floor(Math.random() * 10);` returns a random integer from 0 to 9
  - Math.floor(x) returns the value of x rounded down to its nearest integer
- Alert()
- Prompt()
- array.push()
- array.pop()
- array.sort()

---

## Exercises

**RECAP:** [Coding style and best practices](./01-js-basics-lesson-1.md#coding-style-and-best-practices)

Create separate `.html` and `.js` files for the tasks.

### Task 1

Write an application that creates two lottery rows for next weekend’s Lottery

- Finnish Lottery: 7 numbers between 1 and 40
- use Math.random()
- use arrays for storing rows
- No need to check if there is same number twice, no need to arrange numbers

### Task 2

Write a function that finds the smallest value stored inside an array.

- input parameter is the whole array
- return value is the minimum value
- use of built-in Math.min() function is forbidden

### Task 3

Develop your lottery application (continue task 1):

- User will be prompted how many lottery rows she would like to have
- Pass the amount of rows to a function that will create number of rows based on the passed parameter

### Task 4

Develop your lottery application (continue task 3):

- row creation function should not use the same number twice
- use [array.includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) for checking duplicate numbers
- use while loop until the row is ready (array.length )

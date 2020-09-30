# Orientation Course - Basics of JavaScript Programming 1

MP 9/2020

## Development Tools

### Code editor: [Visual Studio Code](https://code.visualstudio.com/)

(Ultimately, it's your choice but VSCode is recommended)

- free & open source code editor by Microsoft (**!=** Visual Studio IDE)
- wide extension support (JS language support is built-in)
- lightweight, multiplatform support
- good [docs & instructions](https://code.visualstudio.com/docs/editor/codebasics)
- the choice of many JS developers

### VSCode - Basic Usage

Active **project** is the folder open on the left side panel (_File -> Open folder..._)

Handy keyboard shortcuts (for finnish keyboard layout, check _File -> Preferences -> Keyboard shortcuts_ for more)

- Multiline comment: _ctrl-'_
- Delete line: _ctrl-shift-k_
- Move line(s): _alt-up/down_
- Copy line(s): _alt-shift-up/down_
- Auto format code: _alt-shift-f_
- Open integrated console: _ctrl-ö_
- [Command palette](https://code.visualstudio.com/docs/getstarted/tips-and-tricks#_command-palette): _ctrl-shift-p_
- Quick find/open files: _ctrl-p_
- Split editor: _ctrl-§_

[Visual Studio Code Tips and Tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks)

### Web browser for running and testing the code

- Chrome & [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/)
- keep **always** the dev tools console open when developing JS

### Using a local web server for development

- code behaves just like published on a 'real' server in the internet (no direct access to computer's filesystem)
- no need for upload the code to the server (or even refresh the browser) all the time
- no need to publish incomplete, buggy versions of your code
- development can be done in offline mode too
- the url address of the local web server is always `http(s)://localhost:[PORT]` when connecting from the same local computer (ip address `127.0.0.1` works too)
  - `[PORT]` number is defined in the web server settings, something like 8080, 8081, 3000, 3001, 5000, 5050 or 18001 might be the default setting
- [Live Server by Ritwick Dey](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) is a popular extension for VSCode to get an easy to use local dev enviroment

---

## About Java/ECMAScript

- _ECMAScript_ is a specification standardized by _European Computer Manufacturers Association (ECMA)_ for _JavaScript_ language
- ES6 is short for ECMAScript 6, also known as ES2015
- ES8 is short for ECMAScript 8, also known as ES2017 and so on..
- ES6+ versions are often considered "modern JavaScript"
- some selected new features in "modern" ES versions:
  - `const`
  - `let`
  - arrow functions
  - for-of loop

In this material, _JS_ refers just to the modern version(s) of the JavaScript language we are using in this course.

## Getting Started with JS programming

### Interactive application

1. Reads input(s) from a user or users
2. Does something with the input value(s)
3. Displays the result(s

In JS app input can be read for example by prompting from the user, using HTML forms or just by reading user's keyboard presses and mouse movements.

Application output (what the app does) is dependent on user input. For example a really simple sum calculator app would take two numbers as input, add them together and display the result.

### Managing data values: Variable

- a variable is a 'named storage' for data
- variables are declared by using the _keywords_: `const` or `let` (or old ~~`var`~~ which should never be used in modern JS)
- Note: [JavaScript _keywords_](https://www.w3schools.com/js/js_reserved.asp) are reserved words that can't be used for example in variable names.

    ```js
    let someText;
    let someNumber;
    let isTheWorldFlat;
    // Or the same using on one statement:
    let someText, someNumber, isTheWorldFlat;
    ```

- values are assigned to variables using the assingment _operator_ **_=_**:

    ```js
    someText = 'This is some text content stored into variable called someText (the value of the variable)';
    someNumber = 9;
    isTheWorldFlat = false;
    ```

- variable can be declared and value assigned in a one _statement_:

    ```js
    let someText = 'This is some text content stored into variable called someText (the value of the variable)';
    let someNumber = 9;
    const isTheWorldFlat = false;
    ```

- the value stored in a variable can be altered

    ```js
    someText = 'This is the new text.';
    someNumber = 9998;
    isTheWorldFlat = false;
    ```

- except values of the variables defined with `const` (constant) keyword can't be changed:

    ```js
    isTheWorldFlat = true; // illegal operation => produces an error when executed
    ```

- common convention is to always use `const` when changing the value is not necessary
- spaces or other special characters can't be used in variable names

- _statement_ is a one command, instruction given to be executed by the [JavaScript engine](https://en.wikipedia.org/wiki/JavaScript_engine). In JS (and in many other programming languages) a statement ends with a semicolon `;`. In JS `;` is not mandatory because JS engine can insert them automatically. If you choose not to use them you should be familiar with [the automatic insertion rules](https://flaviocopes.com/javascript-automatic-semicolon-insertion/). In this course the use of semicolons is preferred.
- [comments](https://en.wikipedia.org/wiki/Comment_(computer_programming)) in JS are full or partial lines in the code that are not executed
  - code after double slashes `//` or between `/*` and `*/` is treated as a comment

      ```js
      /*
      This
      is a
      multiline comment and not executed.
      */

      let x = 5;   // <- that will be executed
      // let y = 6;  this will NOT be executed at all
      ```

### Types of the variables/values

The type system in JavaScript is loose and dynamic. Type of a variable depends on the type of value currently assigned to it. Built-in types are:

- String (values inside quotes, e.g: `'some text'` or `"some text"` or backticks \``some text`\`
- Number (values can be integers, e.g: `97` or floating point numbers, e.g: `79.234`)
- Boolean (value is `true` or `false`)
- (...and Object, undefined, null, Symbol)

```js
> let a = 13;
> a
13
> typeof a
'Number'
```

### Operators

Assignment operator `=` is just for assigning values to variables: `let x = 5;`

#### Arithmetic

| Operator | Name | Example |
| ------------- | ------------- | ------- |
| `+` | Arithmetic Addition | x=y+2 |
| `-` | Subtraction | x=y-2 |
| `*` | Multiplication | x=y*2 |
| `/` | Division | x=y/2 |
| `**` | Exponentiation | x = a**b |
| `%` | Modulus (division remainder) | x=y%2 |
| `++` | Increment |  x++ |
| `--` | Decrement |  x-- |

#### Strings

With string values the `+` operator is used to add (concatenate) values.

```js
let first = 'John';
let last = 'Doe';
let full = first + ' ' + last; // -> "Jon Doe"
```

Same string concatenation using [Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals):

```js
let full = `${first}  ${last}`; // -> "Jon Doe"
```

Note: If you add a number and a string, the result will be a string:

```js
let sum = "6" + 8; // -> "68"
var text = "Hi" + 5; // -> "Hi5"
```

#### Comparison and logical operators

Comparison of two values evaluates always to `true` of `false` boolean result value.

| Operator | Name |
| ------------- | ------------- |
| == | equal to |
| === | equal value and equal type |
| != | not equal |
| !== | not equal value or not equal type |
| > | greater than |
| < | less than |
| >= | greater than or equal to |
| <= | less than or equal to |
| ? | ternary operator |
| && | logical and |
| \|\| | logical or |
| ! | logical not |

Some examples:

```js
6 == 6;
// true

6 == '6';
// true

6 === '6';
// false

let number = 6;
number === 6;
// true

let word='hello';
word === 'hello';
// true

word !== 'hello';
// false

6 < 7;
// true

6 > 7;
// false

true && true
// true

true && false;
// false

(1 === 1) && ('m' === 'm');
// true

true || false;
// true

(1 === 2) || ('m' === 'm');
// true

false || false
// false

true ? 'this is true' : 'this is false';
// "this is true"

(1 === 2) ? 'this is true' : 'this is false';
// "this is false"
```

### Control structure: Conditional statements

When writing code, we usually want to control the application logic/flow based on a different decisions. And decisions are made based on variables and values. Conditional statements are used for this.

- Use if to specify a block of code to be executed, if a specified condition is true
- Use else if to specify a new condition to test, if the first condition is false
- Use else to specify a block of code to be executed, if the same condition is false

Code blocks are defined using curly braces `{` `}`.

```js
if (condition) {
  //  block of code to be executed if the condition is true
}

// Example:
let message = 'Expensive!';
let price = 9;
if (price < 10) {
  message = 'Price is cheap!';
}
// -> value of message: "Price is cheap!"


if (condition) {
  //  block of code to be executed if the condition is true
} else {
  //  block of code to be executed if the condition is false
}

// Example:
message = '';
price = 8;
if (price < 10) {
  message = 'Price is cheap!';
} else {
  message = 'It\'s expensive!';
}
// -> value of message: "It's expensive!"


if (condition1) {
  //  block of code to be executed if condition1 is true
} else if (condition2) {
  //  block of code to be executed if the condition1 is false and condition2 is true
  //  it's possible to repeat this else if block as many times as necessary
} else {
  //  block of code to be executed if the condition1 is false and condition2 is false
}

// Example:
message = '';
price = 12;
if (price < 10) {
  message = 'Price is cheap!';
} else if (price < 15) {
  message = 'Price is ok.';
} else {
  message = 'It\'s expensive!';
}
// -> value of message: "Price is ok."
```

The [`switch` statement](https://www.w3schools.com/js/js_switch.asp) is an another method to code similar behaviour.

### Type conversions

- String conversion

    ```js
    let number = 25;
    let numberAsAString = String(number); // -> "25"
    ```

- Numeric conversion

    ```js
    let numberAsAString = "22";
    let number = Number(numberAsAString); // -> 22
    ```

- when comparing values, convert the values to the same type first

### Adding JS functionality to web page

In HTML, JavaScript code is inserted between `<script>` and `</script>` tags which can be located inside the `<head>` or `<body>` section of a page:

```html
...
<head>
  ...
  <script>
  console.log("Hello from the html!");
  </script>
</head>
...
```

Or the preferred way: create a separate file for the JS code and link to that file from your html file:

```html
<script src="my-code.js"></script>
```

_my-code.js_ file:

```js
console.log("Hello from the JS file!");
```

The _console.log()_ method writes a message or a value of any type of JS variable to the console. Remember to keep the browser developer tools and console always open when developing JS.

### Simple interactions with user

Both of these are built-in functions to open a pop-up box in front of the browser window.

- _alert()_ can be useful for debugging in some cases (console.log is still the preferred output method)

```js
alert("This is alert");
```

- _prompt()_ can be used to ask some input from a user
  - When a prompt box pops up, the user will have to click either "OK" or "Cancel" to proceed after entering an input.
  - If the user clicks "OK" the box returns the input value as a string. If the user clicks "Cancel" the box returns `null`. The user input can be stored into variable using the assignment operator `=`:

```js
const userAnswer = prompt('What is you favorite colour?', 'black');
```

- _confirm()_ can be used to ask confirmation of something from a user
  - the user will have to click either "OK" or "Cancel"
  - returned value is either `true` or `false` based on the user choice

```js
const userAswer = confirm('Are you sure?');
```

### Coding style and best practices

Following good coding practices makes your application a lot more easier to maintain, develop and understand:

- Use meaningful and descriptive names for variables, functions, etc.
- Use `const` and `let` for variable declarations, do _not_ use `var`
- Be consistent with naming conventions, indentation, commenting style, application structure, file & folder organisation, e.g:
  - indentation: 2 spaces
  - variable & function names: use _camelCase_
- Use proper commenting when needed
- Line length: avoid writing horizontally long lines of code
- Avoid large code files, split to smaller modules

Start small. Take small steps. Test your code all the time, after writing just a few more code lines.

Remember that coding is like handcraft skill, learned by doing, not reading.

---

## Exercises

Create separate `.html` and `.js` files for the tasks.

### Task 1

Task’s purpose is to get your hands "dirty" with JS.

1. Declare two variables `myage` and `yourage` and assign them initial values.
2. Write to console log:
    - "My age is " and the value of `myage`
    - "Your age is " and the value of `yourage`
3. Compare myage and yourage using `if ... else` and based on comparison write to console log who is older (me or you)

### Task 2

Some mathematics. Write a program that

1. asks for a radius of a circle
2. calculates the circumference and the area of the circle
3. prints the calculated values to console
    - "The circumference of the circle is " ...
    - "The area of the circle is " ...

- TIP: Check JS [Math object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)
- NOTE: user inputs by `prompt()` are always string type, convert values to numbers when used as numbers

### Task 3

Password prompt. Write a program that

1. Asks user for a password
2. Compares user input to 'hardcoded' password value
3. Based on the result of the comparison, writes to console: "Welcome in!" or "Wrong password"

### Task 4

Wallet balance and bus ticket. Write a program that

1. asks the amount of money user has
2. asks the price of bus ticket
3. checks if user has enough money for the ticket
     - if there is enough money, subtract the price from the user's total balance and wish a good trip (print to console)
     - otherwise, keep the money and tell user to walk (print to console)
     - in anycase, print user's final amount of money to the console

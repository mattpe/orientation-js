# Orientation Course - Basics of JavaScript Programming 4

MP 9/2020

## JavaScript basics, lesson 4

### JavaScript Objects

[Eloquent JavaScript: Data Structures - Objects and Arrays](https://eloquentjavascript.net/04_data.html)

[MDN web docs: JavaScript object basics](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics)

- Most things are objects in Javascript
- Even primitive values like numbers and string are treated as objects having methods and properties:
  - `'AbbaACDC'.toLowerCase()` -> "abbaacdc"
  - `'n letter string'.length` -> 15
  - `(6.16).toFixed()` -> 6
- Fundamentally objects are key-value pairs

### Creating objects

Object literal notation:

```js
const emptyObject = {};

const person = {
  firstname: 'Calle',
  lastname: 'Wirtanen'
};

console.log(person); // -> {firstname: "Calle", lastname: "Wirtanen"}

const someDog = {
  name: 'Maddy',
  weight: 7,
  breed: 'Cocker Spaniel',
  // NOTE: this keyword doesn't work with arrow functions
  bark: function() {
    if (this.weight < 8) {
      console.log('Wuf.');
    } else {
      console.log('WUFF!');
    }
  }
};

// Adding properties to an empty object
const otherDog = {};
otherDog.name = "Victor";
otherDog.bark = function() {
  console.log("Bark!");
};
```

(Other way to create similar objects by using a constructor function:)

```js
function Dog(name, weight, breed) {
  this.name = name;
  this.weight = weight;
  this.breed = breed;
  this.bark = () => {
    if (this.weight < 8) {
      console.log('Wuf.');
    } else {
      console.log('WUFF!');
    }
  };
}
const harryDog = new Dog('Harry', 7, 'bulldog');
const fifiDog = new Dog('Fifi', 12, 'beagle');
```

(NOTE: (Especially if you are familar with some object oriented programming languages like Java or C#) In JavaScript functions, [`this`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) keyword behaves a little differently compared to other languages. It also has some differences between [strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) and non-strict mode.)

### Some built-in objects

We have been using many objects already.

- all [_strings_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) and [_arrays_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) are objects too (they have properties and methods)

    ```js
    const myArray = ['1', 2, false];
    myArray.length; // -> 3
    myArray.push('fourth item'); // -> (4) ["1", 2, false, "fourth item"]
    'hello world'.length // -> 11
    'hello world'.split(' '); // -> (2) ["hello", "world"]
    ```

- [`console`](https://developer.mozilla.org/en-US/docs/Web/API/Console) - object provides access to the browser's debugging console
- `document` - provides access to the DOM (check lesson 3)
- `event` - object provides information about an event occured in DOM (check lesson 3)
- [`Math`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math) - has properties and methods for mathematical constants and functions
- [`Date`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) - represent a single moment in time in a platform-independent format
  - `Date.now()` - returns a "timestamp", a Number that represents milliseconds since 1 January 1970 UTC ([UNIX Epoch time](https://en.wikipedia.org/wiki/Unix_time))
- [`location`](https://developer.mozilla.org/en-US/docs/Web/API/Location) - represents the location (URL) of the object it is linked to

#### Prototypes

[MDN web docs: Object prototypes](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes)

- Javascript is a prototype-based language (cf. Object-oriented programming (OOP) languages: Java, C#, etc.)
- Prototypes are the mechanism by which JavaScript objects inherit features from one another.
- Almost all objects in JavaScript are instances of [`Object`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
- Typical object inherits properties and methods from `Object.prototype`, e.g. basically all objects are having the `toString()` method

```js
[1, 3, 5, 7].toString(); // -> '1,3,5,7'
person.toString(); // -> "[object Object]"
```

---

## Exercises

Create separate `.html` and `.js` files for the tasks.

### Task 1

Write an application (html & js files) that holds information about two persons (name, age and home country) and prints the information onto the web page (Person name is X years old and lives in [home country]).

1. store person data in objects
1. store persons to an array
1. use a loop to display all persons on the web page (add the list of persons (contents of the array) to the DOM)

### Task 2

Continue from task 1 and add functionality for adding more persons.

1. Add input fields and a button to html file:

    ```html
    <h2>Add new</h2>
    <input placeholder="Name" type="text"><br>
    <input placeholder="Age" type="text"><br>
    <input placeholder="Home country" type="text"><br>
    <button>Add</button>
    ```

1. when input fields are filled and button clicked, new person object is created and added to the existing persons array
    - example for reading the value from the first `<input>` field:

    ```js
    // get referece array to all <input>s
    const myInputs = document.querySelectorAll('input');
    // use array index number to choose one of the <input>s
    const valueOfTheFirstInput = myInputs[0].value;
    ```

1. person list on the page is updated every time when a new person is added

- EXTRA: validate user inputs (name and country can't be empty and type of the age must be number)

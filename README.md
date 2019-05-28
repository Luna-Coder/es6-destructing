# ES6-Destructuring, Spread, & Rest Operators

### Rest Operator with Function Parameters
```js
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}

console.log(howMany(0, 1, 2));                            // You have passed 3 arguments
console.log(howMany("string", null, [1, 2, 3], { }));     // You have passed 4 arguments.
```
ES6 introduces the `rest` operator for function parameters. 

With the `rest` operator, you can create functions that take a variable number of arguments. 

These arguments are stored in an array that can be accessed later from inside the function.

The `rest` operator eliminates the need to check the args array and allows us to apply `map()`, `filter()` and `reduce()` on the parameters array.

___

### Spread Operator to Evaluate Arrays In-Place
```js
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);     // returns 89
```
ES6 introduces the `spread` operator, which allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.

`...arr` returns an unpacked array. In other words, it _spreads_ the array.

However, the `spread` operator only works _in-place_, like in an argument to a function or in an array literal.

___

### Destructuring Assignment to Assign Variables from Objects
```js
let student = { 
                fname: "Erik", 
                lname: "Carr", 
                idNum: 1234 
              };
```

ES5
```js
let fname = student.fname;      // fname = "Erik"
let lname = student.lname;      // lname = "Carr"
let idNum = student.idNum;      // idNum = 1234
```

ES6
```js
const { fname, lname, idNum } = student;
```
The `destructuring` assignment is special syntax for neatly assigning values taken directly from an object to variables.

___

### Destructuring Assignment to Assign Variables from Arrays
```js
const [a, b] = [1, 2, 3, 4, 5, 6];

console.log(a, b);         // 1, 2
```

We can also access the value at any index in an array with `destructuring` by using commas to reach the desired index.
```js
const [a, b,,, c] = [1, 2, 3, 4, 5, 6];

console.log(a, b, c);     // 1, 2, 5
```
ES6 makes destructuring arrays as easy as destructuring objects.

One key difference between the `spread` operator and array `destructuring` is that the `spread` operator unpacks all contents of an array into a comma-separated list. 

Consequently, you cannot pick or choose which elements you want to assign to variables.

___

### Destructuring Assignment with the Rest Operator to Reassign Array Elements
```js
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];

console.log(a, b);    // 1, 2
console.log(arr);     // [3, 4, 5, 7]
```
Variables `a` and `b` take the first and second values from the array. 
After that, because of `rest` operator's presence, `arr` gets rest of the values in the form of an array.

In some situations involving array destructuring, we might want to collect the rest of the elements into a separate array.

The `rest` element only works correctly as the last variable in the list. As in, you cannot use the `rest` operator to catch a subarray that leaves out last element of the original array.

___

### Destructuring Assignment to Pass an Object as a Function's Parameters
```js
const profileUpdate = (profileData) => {
  const { name, age, nationality, location } = profileData;
  // do something with these variables
}
```
In some cases, you can destructure the object in a function argument itself.

This effectively destructures the object sent into the function. This can also be done _in-place_.
```js
const profileUpdate = ({ name, age, nationality, location }) => {
  /* do something with these fields */
}
```
This removes some extra lines and makes our code look neat.

This has the added benefit of not having to manipulate an entire object in a function; only the fields that are needed are copied inside the function.

___

###  Strings using Template Literals
```js
const person = {
  name: "Zodiac Hasbro",
  age: 56
};

// Template literal with multi-line and string interpolation
const greeting = `Hello, my name is ${person.name}!
I am ${person.age} years old.`;

console.log(greeting);
// Hello, my name is Zodiac Hasbro!
// I am 56 years old.
```
A new feature of ES6 is the `template literal`. This is a special type of string that makes creating complex strings easier.

Template literals allow you to create multi-line strings and to use string interpolation features to create strings.

___

### Concise Object Literal Declarations Using Simple Fields
ES5
```js
const getMousePosition = (x, y) => ({
  x: x,
  y: y
});
```
ES6 adds some nice support for easily defining object literals.

ES6 provides the syntactic sugar to eliminate the redundancy of having to write `x: x`. You can simply write `x` once, and it will be converted to `x: x` (or something equivalent) under the hood.

ES6
```js
const getMousePosition = (x, y) => ({ x, y });
```

___

### Concise Declarative Functions with ES6
ES5
```js
const person = {
  name: "Taylor",
  sayHello: function() {
    return `Hello! My name is ${this.name}.`;
  }
};
```
With ES6, You can remove the `function` keyword and colon altogether when defining functions in objects. Here's an example of this syntax:

ES6
```js
const person = {
  name: "Taylor",
  sayHello() {
    return `Hello! My name is ${this.name}.`;
  }
};
```

---

### Class Syntax to Define a Constructor Function
ES5
```js
var SpaceShuttle = function(targetPlanet){
  this.targetPlanet = targetPlanet;
}
var zeus = new SpaceShuttle('Jupiter');
```
ES6 provides a new syntax to help create objects, using the keyword `class`.

This is to be noted, that the `class` syntax is just a syntax, and not a full-fledged class based implementation of object oriented paradigm, unlike in languages like Java, or Python, or Ruby etc.

In ES5, we usually define a constructor function, and use the `new` keyword to instantiate an object.

The `class` syntax simply replaces the constructor function creation.

ES6
```js
class SpaceShuttle {
  constructor(targetPlanet){
    this.targetPlanet = targetPlanet;
  }
}
const zeus = new SpaceShuttle('Jupiter');
```
Notice that the `class` keyword declares a new function, and a `constructor` was added, which would be invoked when `new` is called - to create a new object.

___





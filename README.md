# ES6-Syntax & Features

### Rest Operator With Function Parameters
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

### Spread Operator To Evaluate Arrays In-Place
```js
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);     // returns 89
```
ES6 introduces the `spread` operator, which allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.

`...arr` returns an unpacked array. In other words, it _spreads_ the array.

However, the `spread` operator only works _in-place_, like in an argument to a function or in an array literal.

___

### Destructuring Assignment To Assign Variables From Objects
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

### Destructuring Assignment To Assign Variables From Arrays
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

### Destructuring Assignment With The Rest Operator To Reassign Array Elements
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

### Destructuring Assignment To Pass An Object As A Function's Parameters
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

###  Strings Using Template Literals
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

### Concise Declarative Functions With ES6
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

___

### Class Syntax To Define A Constructor Function
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

### Differences Between import And require
```js
import { functionName } from "./file_path_goes_here";    // We can also import variables the same way
```
In ES5, the function `require()` was used to import the functions and code in external files and modules. However, as some files and modules are rather large, this method wouldn't be practical in those cases.

ES6 gives us a very handy tool known as `import`. Now, we can choose the parts of a module or file to load into a given file, saving time and memory.

Note:
In most cases, the file path requires a `./` before it; otherwise, node will look in the `node_modules` directory first trying to load it as a dependency.

___

### The export Syntax To Reuse A Code Block
```js
const capitalizeString = (string) => {
  return string.charAt(0).toUpperCase() + string.slice(1);
}

export { capitalizeString }      //How to export functions.
export const foo = "bar";        //How to export variables.
```
This is what we refer to as a _named export_. With this, we can import any code we export into another file with the `import` syntax.

When we want some code - a function, or a variable - to be usable in another file, we must export it in order to import it into another file.

If you'd like to compact all your `export` statements into one line, you can take the following approach:
```js
const capitalizeString = (string) => {
  return string.charAt(0).toUpperCase() + string.slice(1);
}

const foo = "bar";

export { capitalizeString, foo }
```

___

### Import Everything From A File With *
```js
import * as myMathModule from "./math_functions";

myMathModule.add(2,3);
myMathModule.subtract(5,3);
```

General Format:
```js
import * as object_name from "./file_path";

object_name.functionName();
```
You may use any name following the `import * as` portion of the statement. 

In order to utilize this method, it requires an object that receives the imported values. From here, you will use the dot notation to call your imported values.

___

### Export Fallback With export default
```js
export default function add(x,y) {
  return x + y;
}
```
With a _named export_, you're allowed you to make multiple functions and variables available for use in other files.

There is another `export` syntax you need to know, known as `export default`. 

Usually you will use this syntax if only one value is being exported from a file. It is also used to create a fallback value for a file or module.

Note: 
Since `export default` is used to declare a fallback value for a module or file, you can only have one value be a default export in each module or file. 

Additionally, you cannot use `export default` with `var`, `let`, or `const`.

___

### Import A Default Export
```js
import add from "math_functions";

add(5,4);     // Will return 9
```
It is important to note that, to import a `default export`, you need to use a different `import` syntax.

The syntax differs in one key place - the imported value, `add`, is not surrounded by curly braces, `{ }`. 

Unlike exported values, the primary method of importing a `default export` is to simply write the value's name after `import`.

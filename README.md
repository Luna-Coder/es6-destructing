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

With the rest operator, you can create functions that take a variable number of arguments. 

These arguments are stored in an array that can be accessed later from inside the function.

The rest operator eliminates the need to check the args array and allows us to apply `map()`, `filter()` and `reduce()` on the parameters array.

___

### Spread Operator to Evaluate Arrays In-Place
```js
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);     // returns 89
```
ES6 introduces the `spread` operator, which allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.

`...arr` returns an unpacked array. In other words, it _spreads_ the array.

However, the spread operator only works in-place, like in an argument to a function or in an array literal.

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

We can also access the value at any index in an array with destructuring by using commas to reach the desired index.
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
This effectively destructures the object sent into the function. This can also be done in-place.
```js
const profileUpdate = ({ name, age, nationality, location }) => {
  /* do something with these fields */
}
```
This removes some extra lines and makes our code look neat.

This has the added benefit of not having to manipulate an entire object in a function; only the fields that are needed are copied inside the function.

# Javascript Daily
JS concepts 

---

**Note:** This repository is specific to Javascript, For react, check [Learning React] (https://github.com/shrik411/react-tuts)

---
### Table of Contents

| No. | Topic |
| --- | ----- |
|1  | [JavaScript](#javaScript) |
|2  | [Object Oriented JavaScript](#object-oriented-javaScript) |
|3  | [TypeScript](#typeScript) |
|4  | [Angular](#learn-angular) |
|5  | [NgRx](#ngrx) |
|7  | [Links for in-depth reference](in-depth-reference) |

## Javascript

- ### Closure

A closure is a function having access to the parent scope, even after the parent function has closed.

```
const add = (function () {
  let counter = 0;
  return function () {counter += 1; return counter}
})();

add();
add();
add();
```

- ### Hoisting (https://www.digitalocean.com/community/tutorials/understanding-hoisting-in-javascript)

JavaScript hoists variables declared with es6 let and const. The difference in this case is how it initialises them. Variables declared with let and const remain uninitialised at the beginning of execution whilst variables declared with var are initialised with a value of undefined.

Function declarations are hoisted.
Function expressions, however are not hoisted.

```
expression(); // Ouput: TypeError: expression is not a function

var expression = function hoisting() {
  console.log('Will this work?');
};

```
The variable declaration var expression is hoisted but it’s assignment to a function is not. Therefore, the intepreter throws a TypeError since it sees expression as a variable and not a function.

Order of precedence

Variable assignment takes precedence over function declaration
Function declarations take precedence over variable declarations

```
var double = 22;

function double(num) {
  return (num*2);
}

console.log(typeof double); // Output: number

var double;

function double(num) {
  return (num*2);
}

console.log(typeof double); // Output: function

```

Class declarations

Much like their function counterparts, JavaScript class declarations are hoisted. However, they remain uninitialised until evaluation. This effectively means that you have to declare a class before you can use it.

- ### Strict Mode

This will enable strict mode, only modern features will work, old code will show error and need to be replaced.

to enable write "use strict" on top of the file


- ### Object properties & descriptors
writable
enumerable
configurable

- ### this keyword in Javascript

Functions, in JavaScript can be invoked in multiple ways :
1.Function invocation 
2.Method invocation 
3.Constructor invocation

```
let add = {
            num: 0,
            calc: function () {

                // logs the add object
                document.write(this + ' ')

                function innerfunc() {
                    this.num += 1;

                    // logs the window object
                    document.write(this + ' ');

                    return this.num

                } return innerfunc();
            }
        };

```

'this' inside inner function refers to the window object, values from outer function if defined as method invocation are not available hence will return NaN
solution is to assign reference to variable which can be used later in innerfunction.

-- this with constructor invocation:
Constructor invocation is performed when new keyword is followed by an function name
For example: let person1= new People(‘John’, 21); 

- ### Indexed & Keyed collections
Array

```
var colors = ['red', 'green', 'blue'];

colors.forEach(color => console.log(color)); 

// red
// green
// blue
```

Array methods
...- concat
...- join
...- push
...- pop
...- shift
...- unshift
...- slice(start_index, upto_index)
...- splice(start_index, upto_index)
```
var numbers = new Array('1', '2', '3', '4', '5');
numbers.splice(1, 3, 'a', 'b', 'c', 'd'); 
// numbers is now ["1", "a", "b", "c", "d", "5"]
// This code started at index one (or where the "2" was), 
// removed 3 elements there, and then inserted all consecutive
// elements in its place.
```
...- reverse
...- sort
...- map
...- filter
...- indexOf

- ### Map, reduce & filter:

...map()
Use it when: You want to translate/map all elements in an array to another set of values.


...filter()
Use it when: You want to remove unwanted elements based on condition.
Example: remove duplicate elements from an array.

...reduce()
Use it when: You want to find a cumulative or concatenated value based on element across the array.
Example: Sum up orbital rocket launches in 2014

- ### Memory management

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_Management
Garbage collection

Mark-and-sweep algorithm

node --max-old-space-size=6000 index.js

We can also expose the garbage collector for debugging memory issues using a flag and the Chrome Debugger
node --expose-gc --inspect index.js

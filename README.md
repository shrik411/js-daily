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
|7  | [Links for in-depth reference] (in-depth-reference) |

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

# W1D4 Callbacks!

### Summary
1. [Functions as values](#functions-as-values)
2. [Callbacks and higher order functions](#callbacks-and-higher-order-functions)
3. [Anonymous functions](#anonymous-functions)
4. [Arrow functions](#arrow-functions)
5. [Make our own higher order function](#make-our-own-higher-order-function)

### Functions as values
Function declarations are hoisted, which is bad coding practice, whereas function expressions are not.

```javascript
// function declaration
function helloName(name) {

}
// function expression
const helloName = function(name) {

}
```

Since functions are objects, we can treat them as such.

```javascript
const helloName = function(name) {

};
let helloName.secretMessage = "hello";
console.log(helloName.secretMessage); //output: "hello"
```

If functions are objects, we can put it in an array!

```javascript
const funcs = [sayHello];
funcs[0]('dean');
```

> Use for..of with every **except** objects, because Of and Object both start with 'O'

In for..of loops, **always** declare the variable or else js will make it global.


### Callbacks and higher order functions

Can we pass a function to a function?

```javascript
const sayHello = function(name) {
  console.log(`hello there ${name}`);
}

// runMyFunc = HOF & func = callback
const runMyFunc = function(func) {
  console.log(func);
  console.log(func.toString());
  func('dean');
}

runMyFunc(sayHello); // => "[Function: sayHello]" and function definition, then "hello there dean"
```

A *callback* is a function that gets passed to another function to be used within.

A *higher order function (HOF)* is a function that accepts another function as an argument OR a function that returns another function.


### Anonymous functions
Any value can be anonymous.

```javascript
const username = 'Alice'; //Name of Alice is username
console.log(username);

console.log('Bob');       //Name is anonymous.
```

Anonymous values are values without a key.

If you're never going to use a value or function again, make it anonymous. There's no point of having it in memory.

### Arrow functions

Included in ES6 (ecma script 6), which came out in 2015.

What is an arrow function?
```js
const sayHello = function(name) {
  return `hello there ${name}`;
};

const sayHello2 = name => `hello there ${name}`;
```
Advantages:
1. No function keyword
2. No parentheses if only one argument
3. If only one line of code, 
  - no brackets are needed
  - code is implicitly returned
4. Great for callbacks

### Make our own higher order function

Why do we use higher order functions?
- To seperate out what is happening in our code.
- Functions should have a single purpose.
  - Try to avoid ever saying "and" in describing your functions.

```js
const names = ['alice', 'bob', 'carol', 'dean', 'elise'];

const doOnEveryIteration = name => {
  const output = `hello there ${name}`;
  console.log(output);
};

const iterateThroughAnyArray = (arr, callback) => {
  for (const element of arr) {
    callback(element);
  }
};

iterateThroughAnyArray(names, doOnEveryIteration);
```
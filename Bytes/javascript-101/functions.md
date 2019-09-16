# Functions
Functions are one of the fundamental building blocks in JavaScript. A function is a block of code designed to perform a particular task in a repeatable way.

A function is in essence a mini-program inside of your program.

For example instead of writing
```js
const average = (1 + 2 + 3) / 3;
const average2 = (5 + 2 + 6) / 3;
const average3 = (8 + 8 + 8) / 3;
const average4 = (9 + 2 + 3) / 3;
```

we could create a function that calculates the average of three numbers:
```js
function averageOfThreeNumbers(a, b, c) {
  return (a + b + c) / 3;
};
```

Functions can be assigned identifiers, just like literal values can be assigned to variables.

Using the identifier, a function can then be **invoked** whenever that code block is required.

To invoke a function, you append `()` to its identifier.

```js
function averageOfThreeNumbers(a, b, c) {
  return (a + b + c) / 3;
};

const average = averageOfThreeNumbers(1, 2, 3);
const average2 = averageOfThreeNumbers(5, 2, 6);
const average3 = averageOfThreeNumbers(8, 8, 8);
const average4 = averageOfThreeNumbers(9, 2, 3);
```

In this example, the code block is only one line long but it is easy to see that when working with long code blocks, functions are really useful.

## Function definition
Functions are defined using the `function` keyword.
```js
function doSomething (parameter) {
  // some statements
};
```

The above is called a **function declaration**, and creates a function called `doSomething` that has access to a variable called `parameter`

Functions can also be created using a **function expression**:

```js
const doSomething = function(parameter) {
  // some statements
};
```
This does essentially the same thing as the first example. However, using a function expression allows you to create **anonymous functions**: functions with no name. the above function is anonymous, because it is not given a name between the `function` keyword and the parameter list.

Anonymous functions are useful when creating a function to pass as a parameter into another function, such as to an array enumerator.

## Return value
The `return` keyword can be used to stop the execution of the code in the function and provide a value back to the context in which the function was called.

```js
function add(a, b) {
    return a * b;
}

const x = add(4, 3);
```
In the above example, the return value of `add` will be assigned to `x`;

Any code in a function after a return statement will not be executed.

## Function parameters

Parameters are values that get injected into the function as variables, taking their names/identifiers from the parameter name in the function definition.

So writing
```js
function averageOfThreeNumbers(a, b, c) {
  return (a + b + c) / 3;
};

averageOfThreeNumbers(1, 2, 3);
```

is a bit like writing
```js
const a = 1;
const b = 2;
const c = 3;
(a + b + c) / 3;
```

## Function scope
Every function creates its own **scope**. This means that any variables created inside of a function (including the parameters), are not accessible outside of the function.

```js
const foo = 10;

function doSomething() {
  const foo = 50;
  console.log(foo);
};

console.log(foo); // logs 10 - the value of foo outside of the function
doSomething(); // logs 50 - the value of foo inside the function
```

## Arrow functions
Functions can also be created using **arrow syntax**:

```js
const doSomething = (parameter) => {
  // some statements
};
```

This is shorthand for the function expressions above. Arrow functions are a new addition to JavaScript. They are always anonymous.

The main benefit of arrow function is that they allow **implicit returns** for functions that only contains a `return` statement:

```js
const sayHello = name => 'Hello ' + name;
```
is the same as
```js
const sayHello = (name) => {
  return 'Hello ' + name;
};
```

# Callback Functions

In JavaScript, we can pass functions around by reference - that is, we don't have to invoke them straight away. We can also pass them into other functions. A function that has a parameter that accepts another function as an argument is referred to as a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function).

When we refer to a callback function, we mean that we pass a function reference (its definition) into another function as an argument. That other function will execute and at any point can call our passed function, passing arguments if it wishes to do so. 

## Examples

In the below example, `sayBye` gets passed as an argument to `sayHi` (not the function's return value as we haven't called it, but rather the function definition). This argument gets assigned to the parameter `callback`. `callback` now references our original `sayBye` funtion definition, so once we've said hello, we can just call `callback` by adding parentheses `()`:

```js
const sayHi = (callback) => {
  console.log('Hello')
  callback()
}

const sayBye = () => {
  console.log('Bye!')
}

sayHi(sayBye)
// 'Hello'
// 'Bye'
```

There's no reason why we can't invoke (call) callbacks with arguments either. In this scenario we pass `Molly` as an argument that gets assigned to parameter `name`, and we pass `sayBye` as an argument which gets assigned to parameter `callback`. Inside `sayHi` we call `callback` and pass the value assigned to `name`:

```js
const sayHi = (name, callback) => {
  console.log('Hello ' + name)
  callback(name)
}

const sayBye = (name) => {
  console.log('Bye ' + name + '!')
}

sayHi('Molly', sayBye)
// Hello Molly
// Bye Molly!
```

You should always check your callback is a function before trying to call it. You can do so with [typeof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof):

```js
const sayHi = (name, callback) => {
  console.log('Hello ' + name)

  if (typeof callback === 'function') {
    callback(name)
  }
}

const sayBye = (name) => {
  console.log('Bye ' + name + '!')
}

sayHi('Molly', sayBye)
// Hello Molly
// Bye Molly!
```

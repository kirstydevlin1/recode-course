# Objects

Objects group together related data and/or functionality. We refer to an object's data, we usually mean its properties, and when we refer to its functionality, we usually mean its methods.

In JavaScript, objects are essentially the same as what an object is in real life. A car might have 4 wheels and 3 doors, and it can accelerate, brake etc. They are made up of key/value pairs, so you might have a key of `wheels` with a value of `4`.

## Creating a new object

The most common way to create an object in JavaScript is through the _object literal_:

```js
const myObj = {}
```

You can also do (not recommended):

```js
const myObj = new Object()
```

The benefit of using the object literal (`{}`) is that you can define properties and methods on the object at time of creation:

```js
const car = {
  wheels: 4,
  doors: 3,
  drive () {
    console.log('vroom')
  }
}
```

You can also define property/method keys with strings (but it isn't recommended):

```js
const car = {
  'wheels': 4,
  'doors': 3,
  'drive' () {
    console.log('vroom')
  }
}
```

## Difference between properties and methods

A property is just some data stored on the object:

```js
const orange = {
  hasSkin: true
}
```

A method is a function that usually is specific to and/or modifies the object:

```js
const orange = {
  hasSkin: true,
  peel () {
    this.hasSkin = false
  }
}
```

You can access properties on the object inside of methods with the `this` keyword. `this` refers to the object the method has been called on.

Note also that `peel () {}` is shorthand for `peel: function () {}`:

```js
const orange = {
  hasSkin: true,
  peel: function () {
    this.hasSkin = false
  }
}
```

`this` won't equal the object if you assign an arrow function to the property name, so be careful with your syntax.

## Accessing properties/methods

You can access an objects properties/methods with _dot notation_ (`.`):

```js
console.log(car.wheels) // 4
```

You can also use _square bracket notation_, which is good for when you don't know the property name (it could be a user requesting information on a certain property) or for when/if the property name isn't valid JavaScript:

```js
const part = 'wheels'

console.log(car[part]) // 4

const me = {
  'email-address': 'hello@world.com'
}

console.log(me.email-address) // Uncaught ReferenceError: address is not defined
console.log(me['email-address']) // "hello@world.com"
```

Square bracket notation converts whatever is passed between the brackets to a string, before trying to find a matching key on the object.

## Assigning new properties/methods

You can think as properties/methods on an object as variables that are just attached to the object. Assigning is as easy as variable assignment. You just write the same code you would t access a property/method and follow it by an assignment operator:

```js
car.wheels = 3
car.drive = function () {
  console.log('VROOOOOM!')
}
me['email-address'] = 'awesome@email.com'
```

If the key (i.e. `wheels`, `drive`, `email-address`) doesn't exist, then JavaScript will first create it and then assign the value, so objects can be added to.

## Objects can be nested

Objects can also have other objects nested inside of them as property values:

```js
const car = {
  parts: {
    wheels: 4,
    doors: 5
  },
  colour: 'red'
}
```

## You've used dot notation and square bracket notation before

Almost everything in JavaScript is an object. This can be seen with arrays for example where you might call `array.push()` (a method) or you might access an array's length (a property) with `array.length`. You can also retrieve an element in an array via square bracket notation (because to start a variable name with a number is illegal in JS): `array[0]`.

With JavaScript objects you can return the value of a property using dot notation.

For example, to get the value of the `name`property from an object `const person = { name: 'Fred' }`, we would do `person.name`.

Using the constructor pattern, these properties are created on the constructor function itself, and manipulated using methods.

However, for the property we are trying to view - `isAlive` - this function is based on 3 other values `age`, `hunger` and `fitness` - which makes it much harder to keep track of then a simple property like `age`.

One approach we could take to solving this problem is that every time we change the value of `age`, `hunger` or `fitness`, we could also set the `isAlive` property based on the new values of the other properties. In the `walk` function, we could add the following.

```js
Pet.prototype.walk = function() {
  ...
  this.isAlive = this.age < 30 && this.hunger < 10 && this.fitness > 0;
}
```

with the same modification in the `feed` and `growUp` functions.

However, this would quickly get repetitive, and would be quite unmanageable if we wanted to add more features to our Pets.

A better way would be to add an isAlive method to calculate the value. This means we would only have to write the code once, and could extend it easily - that is, if we wanted to add more functions, we would only have to change the code in one place.

```js
Pet.prototype.isAlive = function() {
  return this.age < 30 && this.hunger < 10 && this.fitness > 0;
}
```

However, methods should be actions an object can perform. `isAlive` definitely seems more like it should be a property than an action.

Thankfully there is a bit of magic that provides an ideal solution to the problem we're facing - **getter methods**

Getter methods allow access to a property that returns a dynamically computed value - they are methods that can be used *like* properties - they allow us to report on an objects state, without actually managing a new piece of state.

This is good, because the less state you have to manage, the simpler your code will be.

The syntax for this is a little unusual.

The prototype for an object is itself an object (by default an empty object).

When you create a method (e.g. `Pet.prototype.isAlive = function() {...`), `Pet.prototype` is an object, and you are setting a property on that object.

However, this can't be done with getter methods, as they have to be created on an object literal.

```js
Pet.prototype = {
  get isAlive() {
    return this.age < 30 && this.hunger < 10 && this.fitness > 0;
  }
};
```

This should go after the constructor function definition (`function Pet() {}...`), but before the first method definition. Can you see why? What would happen to the `walk` function in the following example?

```js
function Pet(name) {
  this.name = name;
  this.age = 0;
  this.hunger = 0;
  this.fitness = 10;
}

Pet.prototype.walk = function() {
  this.fitness += 4;
}

Pet.prototype = {
  get isAlive() {
    return this.age < 30 && this.hunger < 10 && this.fitness > 0;
  }
}
```

## [Step 10](../step10.md)

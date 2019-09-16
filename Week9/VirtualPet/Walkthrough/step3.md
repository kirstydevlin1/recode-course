```js
const pet = new Pet('Fido');
pet.name;
```

That code should ideally set the value of `pet.name` as 'Fido'. However - you should have got `undefined` instead.

This is because the `pet` object doesn't have a `name` property.

A good unit test to cover this behaviour might look like this:

```js
describe('constructor', () => {
  ...
  it('sets the name property', () => {
    const pet = new Pet('Fido');
    expect(pet.name).toEqual('Fido');
  });
});
```
Running the test should repoduce the unexpected behaviour you saw in the Node REPL:

```
Expected value to equal:
  "Fido"
Received:
  undefined
```

Again, this failing test is good - it's one more feature covered, and we can now easily see why it's not working as we'd expect.

To fix the error, we need to set a property on the object being created by the `Pet` function:

```js
function Pet(name) {
  this.name = name;
}
```
It is important to note that constructor functions *are* functions, and are not objects themselves. 

When you create an object literal, you would assign properties to an object like so:

```js
const pet = {
  name: 'Fido'
};
```

or you could also set a property on an existing object like this:

```js
const pet = {};
pet.name = 'Fido';
```

When using a constructor function, we have to use the keyword `this`.  
As well as being confusingly-named, `this` is a really tricky topic in JavaScript.  
We will be going into it in more detail in due course, but for now, you need to know that when used in a constructor function, it refers to the object that will be returned by the function.

So in the case of our Pet function, when we write `this.name = name`, `this` refers to the object returned from by calling `new Pet()`, so `this.name` refers to the `name` property of that object.

So our code now allows us to create objects with a given `name` property. That's exactly what we wanted to achieve, so pat yourselves on the back, add, commit and push your code.

## [Step 4](../step4.md)
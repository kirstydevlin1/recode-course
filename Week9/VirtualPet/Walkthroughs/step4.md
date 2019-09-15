To be able to increment the pet's age, we first need to give it an age.

This isn't something we should be able to set manually - whenever we create a new `Pet`, it should have an age of 0.

A feature test in the Node REPL might look like this:

```
> const Pet = require('./src/pet');
undefined
> const pet = new Pet('Fido');
undefined
> pet.age;
0
> pet.growUp();
undefined
> pet.age;
1
```

we would expect the first call to `pet.age` to return 0, but it currently returns `undefined`.

So let's add a unit test to cover this expectation:

```js
describe('constructor', () => {
  ...

  it('has a initial age of 0', () => {
    const pet = new Pet('Fido');
    expect(pet.age).toEqual(0);
  });
});
```

To fix this, you can add an age property to the constructor function with a value of zero:

```js
function Pet(name) {
  this.name = name;
  this.age = 0;
}
```

This should pass the unit test, but if you run the full feature test in the Node REPL again, `pet.growUp()` will throw an error:

```
TypeError: pet.growUp is not a function
```

We can add a unit test to cover this part of the feature too:

```js
describe('growUp', () => {
  it('increments the age by 1', () => {
    const pet = new Pet('Fido');
    pet.growUp();
    expect(pet.age).toEqual(1);
  });
});
```

To fix this, we need to add a **method** to out `Pet` objects.

We can do this in one of two ways: Adding an **instance method** or adding a **prototype method**

Adding an instance method would look like this:

```js
function Pet(name) {
  this.name = name;
  this.age = 0;
  this.growUp = function() {
    this.age += 1;
  };
}
```

Adding the same function as a prototype method looks like this:

```js
function Pet(name) {
  this.name = name;
  this.age = 0;
}

Pet.prototype.growUp = function() {
  this.age += 1;
};
```

These will both solve the problem we're having. The only difference between them is that for the first solution, the method will be re-defined for each instance of `Pet`.

If you have to instances of `Pet`:
```js
const fido = new Pet('Fido');
const rex = new Pet('Rex');
```

Both Fido and Rex will have their own distinct `growUp` functions. Those functions just happen to have the same logic:

```
fido; // { name: 'Rex', age: 0, growUp: [Function] } - both objects have a growUp function
rex; // { name: 'Fido', age: 0, growUp: [Function] }
```

However, we could reassign the value of `growUp` on Rex:

```js
rex.growUp = function () {
  this.age += 5;
}
```

Now calling `rex.growUp` on will make Rex age 5 years, but `fido.growUp` will only add 1 year to Fido's age.

Contrast this to adding a method to `Pet`'s prototype, both Rex and Fido will share the same `growUp` method.

```js
fido; // { name: 'Rex', age: 0 } - neither object has their own growUp function
rex; // { name: 'Fido', age: 0 }

fido.__proto__; // { growUp: [Function] } - both object prototypes have the grow up method
rex.__proto__; // { growUp: [Function] }
fido.__proto__ === rex.__proto___; // true - both objects have the same prototype objects
```
If you change the value of the method on `Pet`'s prototype, that change will occur on all instances of `Pet`.

In practice, this pattern is nearly always what you want:

- Properties should be defined on the object instance (i.e. each object should have it's own age, name etc)
- Methods should be defined on the object's prototype (i.e. each object of the same type should *behave* in the same way)

So add `growUp` as a method on `Pet`'s prototype, then add, commit, push to GitHub.

## [Step 5](../step5.md)
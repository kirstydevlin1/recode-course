Running a feature test for this feature:

```
> const Pet = require('./src/pet');
undefined
> const pet = new Pet('Fido');
undefined
> pet.age;
0
> pet.growUp();
undefined
> pet.growUp();
undefined
> pet.fitness;
4
> pet.walk()
undefined
> pet.fitness
8
> pet.walk()
undefined
> pet.fitness
10
```

What we actually get:
```
>pet.walk()
TypeError: pet.walk is not a function
```

Implementing a unit test:

```js
describe('walk', () => {
  it('increases fitness by 4', () => {
    const pet = new Pet('fido');
    pet.fitness = 4;
    pet.walk();
    expect(pet.fitness).toEqual(8);
  });
});
```

To implement this, we add a function to the `Pet` prototype:

```js
Pet.prototype.walk = function() {
  this.fitness += 4;
}
```

**THEORY TIME**

This function (as well as the `growUp`) function alters the **state** of the Pet instance.

In programming, something has state if:
- it has an identity
- it has a set of values associated with that identity
- the values associated with the identity can change over time

The state of a thing is a snapshop of the values associated with that thing at a point in time.

In JavaScript, objects have state:

```js
const fido = new Pet('fido');
const fido2 = new Pet('fido');
```

In this example, `fido` and `fido2` are both distinct objects, they are seperate entities from each other. So they each have a unique identity.

Both objects have a set of values associated with them (`name`, `fitness`, `age` etc). Because the objects are distinct, the values are associated with that individual object. If we changed the `age` of `fido`, the age of `fido2` would not change.

When the value of `fido`'s age does change, we say it's state has changed.

The idea of a stateful object is in contrast to a fixed value that cannot change - for example the number `9`, or the string `'Hello'`. In 100 years, the value of `9` will still be `9`, for example. If you try to reassign the value of `9` in Javascript (`9 = 10;`, for example), you will get an error.

**END OF THEORY TIME**

Now that we can walk our pet and increase it's fitness, lets run through the feature test again.

The second call to `pet.walk` should now increase the `fitness` property to 11.

This isn't what we wanted. So let's write a unit test.

```js
describe('walk', () => {
  ...
  it('increases fitness by to a maximum of 10', () => {
    const pet = new Pet('fido');
    pet.fitness = 8;
    pet.walk();
    expect(pet.fitness).toEqual(10);
  });
});
```

To fix this, we can use a bit of control flow:

```js
Pet.prototype.walk = function() {
  if ((this.fitness + 4) <= 10 ) {
    this.fitness += 4;
  } else {
    this.fitness = 10;
  }
}
```

And the test should pass.

Now we can do our first bit of refactoring.

Refactoring is the practice of re-writing existing code to improve it's maintainability and readability. As your code projects grow, they will get more complex, and a piece of code you wrote last week may not fit in with the code you're writing today. In such a case, it may be worth refactoring that code to improve the structure of the project as a whole, rather than awkwardly fitting your new code around the existing code.

Refactoring should not affect how software is used externally. One of the big reasosn for writing tests is to ensure that the existing functionality is preserved when refactoring our code.

It's generally good practice to check if you refactor your code every time you make a unit test pass.

In our case we can make our code more readable by removing some **magic numbers**.

A magic number is a number that appears in our code with no context as to what it represents.

Where we have the number 10 in our `walk` function, this represents the maximum value that the Pet's fitness can be. But to another developer coming to work on our code, this might not be immediately clear, especially if the number 10 appears multiple times in our code representing different things.

To fix this, we can add the following line above the `Pet` function definition:

```js
const MAXIMUM_FITNESS = 10;
```

then whenever the number 10 is used in the code to represent the maximum fitness a Pet can have, replace the number `10` with `MAXIMUM_FITNESS`.

Notice that we have kept this number outside of the `Pet` constructor function? This is because it is a constant value, is not part of the `Pet`'s state, so it doesn't need to be set in the constructor.

Can you see any other magic numbers you can replace? If so, replace them. There is no right or wrong answer, it depends on the code you're working on, and how readable you think it is.

Once you've done refactoring, run your tests again to check they still pass, than add, commit and push your code.

## [Step 7](../step7.md)

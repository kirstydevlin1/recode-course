A guard clause is a technique where an `if` statement is placed at the top of a function in order to prevent the function code from modifying state in certain circumstances.

In our case, if the pet is not alive, we don't want to the `walk`, `growUp` and `feed` functions to modify the state of the Pet's `fitness`, `age` or `hunger` properties - we actually want the code to **throw an `Error`**

The `throw` keyword is similar to `return` in that once your code hits a `throw` statement, nothing after it will run. Instead, it will stop the current process from running and create a **run-time exception**.  

These exceptions are useful because they signal that something has gone wrong, and allows you as a developer to handle the failure more elegantly.

You can `throw` anything - numbers, strings etc - but it is best practice to throw an `Error` object.

`Error` is a constructor function that creates an object with `name` and `message` properties. One of the main benefits of throwing an `Error` instead of just a regular string, for example, is that if the `throw` is not caught and handled, then it will also provide you with a **stack-trace**, that is the last files/lines of code that ran before the Error occured. This is really useful for debugging.

We will see more about Error catching/handling later in the course, but for now, we just need to know how to throw one - and test one.

Jest has a built in matcher for testing that an exception is thrown - `toThrow`

We want our functions to `throw` an error if the pet is no longer alive.

So we can try to write a test for this like follows:

```js
describe('feed', () => {
  ...
  it('throws an error if the pet is not alive', () => {
      const pet = new Pet('Fido');
      
      pet.age = 30;
      
      expect(pet.feed()).toThrow('Your pet is no longer alive :(');
    });
  });
});
```

What happens when you run this test?

You should see an error saying `Received value must be a function, but instead "undefined" was found`

Can you guess why this might be?

When using `toThrow`, the value passed to `expect` must be a function. 

By passing `pet.feed()`, we are actually invoking `pet.feed`, we are passing the return value of that function to `expect`, which is actually `undefined`.

The reason for this is that if we invoke an error-throwing function ourselves in the test, it would throw an error before the test had executed, which would cause the test to fail.

Internally, `toThrow` will try to invoke the given function itself to check that an error is thrown.

To change this, we should just avoid invoking the function we want to test:

```js
describe('feed', () => {
  ...
  it('throws an error if the pet is not alive', () => {
      const pet = new Pet('Fido');
      
      pet.age = 30;
      
      expect(pet.feed).toThrow('Your pet is no longer alive :(');
    });
  });
});
```

Running the test should now give usa new error:

```
Expected the function to throw an error matching:
  "Your pet is no longer alive :("
But it didn't throw anything.
```

That error makes more sense, as we've not yet written any code to satisfy the expectation.

Add the following code to the top your `feed` method:

```js
if (!this.isAlive) {
  throw new Error('Your pet is no longer alive :(');
}
```

If you run the test, it should now pass.

To finish your virtual pet, you need to add similar logic to the `walk` and `growUp` functions.

You also need to make the `checkUp` function `return` this same string.

You should be able to test and implement these features now.

Don't forget to refactor, if you can!

Once you've done that, add, comit and push your code.

Congratulations, you made your own virtual pet game from scratch in JavaScript!

## [Optional challenge: Having a baby](../challenge.md)

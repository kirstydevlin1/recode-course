To open the Node REPL:
```
$ node
```

We can use the Node REPL as a sandbox for manually testing out the functionality of our code.

Once the REPL is open, type `const pet = new Pet();`

What did you expect to happen here? We would expect the `Pet` function to return a new object.

You should see an error saying `ReferenceError: Pet is not defined`

This is a failing test - and it's a good thing!

This type of testing is called **feature testing** - we are testing a feature in full, rather than writing unit tests to test an individual part of the code.

In this case, the feature we are trying to implement is that we can create a pet with a given name.

This can be broken into two units:

- the Pet function returns an object
- the returned object has a name property matching the passed `name` argument

When we try to run the code and get unexpected behaviour like this, it can be translated into unit tests, to ensure that our code behaves are we expect it to:

In a new file `__tests__/pet.test.js`, write the following code:

```js
describe('constructor', () => {
  it('returns an object', () => {
    expect(new Pet('Fido')).toBeInstanceOf(Object);
  });
});
```

If you run the test, you should see a similar error: `ReferenceError: Pet is not defined`

The error message that occured can also be used to help us solve the problem:

A reference error occurs when we are trying to use a variable that doesn't exist in the JavaScript runtime memory.

To fix the problem, we're going to have to create a variable with that name.

Of course, if's not much good if the variable only exists in the Node REPL. We want our code to live in a file.

The answer to our problem is `module.exports` and `require`.

- `module.exports` is a built in feature of Node that allows you to expose a piece of code and make it available for use outside of the file that it is written in.

- `require` is another built in feature that allows you to pull in code exported from one file into a different file, and use it there.

Create a new file `src/pet.js` and then at the top of the test file, add the following code:

```js
const Pet = require('../src/pet');
```

The error message before said that we were referencing a variable `Pet` that didn't exist.

This new code has created a variable `Pet`, so we should hopefully see a different outcome when we run the test again:

```
TypeError: Pet is not a constructor
```

This error is another step in the right direction. It's telling us that `Pet` is now recognised, but isn't a constructor function (so we can't use the `new` keyword with it).

A constructor function is just a normal JavaScript function declared with the `function` keyword.

When combined with the `new` keyword, these functions will return an object.

Constructor functions in JavaScript are analogous to classes in more typical object-oriented programming languages. They allow you to create a *type* of object, that has a common set of methods and properties.

In `pet.js`, add the following code:

```js
function Pet() {}

module.exports = Pet;
```

This does two things:

- It defines a **function** `Foo`
- It exports that function from the file

If you run the tests again, it should pass.

Try opening up the node REPL again and running the code at the start of this step again. You will have to use `require` to make the function available, but it should work in the REPL too.

:twisted_rightwards_arrows: Commit your work, push it to GitHub.

## [Step 3](../step3.md)
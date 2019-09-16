# Throwing Errors and Error Handling

In JavaScript, we can use the `throw` keyword to raise a runtime exception. This will stop the code being executed, and instead return the thrown value to the user.

There are a couple of reasons we might want to throw an error:
- To prevent misuse - e.g. passing in a string to a function that expects an integer
- To prevent a function from doing something that it shouldn't - e.g. preventing a user from editing a value in a database without permission

We can `throw` any value, but it is normally good practice to throw an `Error` object using the `Error` constructor function.

## Example
Consider the following code adapted from the `virtual-pet` challenge

```js
function Pet(name) {
  this.name = name;
  this.hunger = 0;
}

Pet.prototype.feed = function feed() {
  if (this.hunger >= 10) {
    throw new Error('Your pet is no longer alive :(');
  }
  this.hunger -= 3;
}

Pet.prototype.checkUp = function checkUp() {
  if (this.hunger >= 10) {
    return 'Your pet is no longer alive :(';
  }

  if (this.hunger > 7) {
    return 'I am hungry';
  }

  return 'I am fine!';
}
```

## Why `throw` instead of `return`?
In the `feed` method, we want to prevent the `hunger` value being changed if the pet isn't alive (i.e. if the hunger level is greater than 10).

We could achieve this using a `return` value, but in this case it would be preferable to use `throw`:

- **Semantics** - `throw` indicates to other developers that this is not the expected behaviour of the function - the responsibility of this function is to change the `hunger` property, not to report on the `Pet`'s status.
- **Signature/Interface consistency** - If everything works as we expect it to, the `feed` method  has no return value (it's return value is `undefined`). If we used a `return` statement in the guard clause, the method's signature (and the interface of the `Pet` constructor) would change - it would sometimes return `undefined`, and sometimes return a string. For the client that is using this code, this adds a level of unpredictability to our `Pet`, which is a bad thing.

In the `checkUp` method, we DO return a string however:
- The responsibility of the method is to report on the `Pet`'s wellbeing - that is exactly what the function is doing
- The expected return value of the method is a string - we are still returning a string, so it's consistent with what the client would expect.

## Why `Error` instead of a string, number etc?
In the `throw` statement in `feed`, we are throwing an `Error` object, rather than a plain string.
A big reason for this is semantics again - seeing `Error` is an indicator that something is happening that shouldn't happen.

Additionally, `Error`'s provide a **stack-trace**

```
Error: Your pet is no longer alive :(
    at Pet.feed (/Users/michaelharrison/Projects/virtual-pet/pet.js:8:11)
```

The stack-trace tells you where the error has occured, and where the code had been before that - in this case, it tells us that the error occured at `Pet.feed`, in the file `pet.js` on line 8.

This information is useful for debugging - instead of just panicking and thinking *AHH MY CODE IS BROKEN* you now have a starting place to find out what's wrong.

Additionally, there are different types of Error constructors, which all extend from the base `Error` constructor. The ones available by default are:
- `EvalError`
- `InternalError`
- `RangeError`
- `ReferenceError`
- `SyntaxError`
- `TypeError`
- `URIError`

[Read about what each of these mean here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error#Description)

Having different error types is useful because it's another indicator to what might have gone wrong.

You can even make your own Error types by extending the `Error` constructor yourself. We might want to make our own `DeadPetError`, for example.

## Error handling
When you are using some code that `throw`s something, you can use a `try...catch` block to `catch` the error (throw, catch, see what they did there?) and handle it in a friendly way.

```js
try {
  pet.feed();
} catch (e) {
  console.log(e.name);
  console.log(e.message);
}
```

Here, we are trying to feed the pet, and if an error is thrown, then we handle the error gracefully in the `catch` block - in this case we are using `console.log` to print the error name (`Error`, `DeadPetError` etc), and the error message (`Your pet is no longer alive :(`)

This prevents the error from making the program crash.

If pet.feed returned a string in the case of an error, our code might look like this:

```js
const error = pet.feed(); // we have to assign the error to a variable, just in case a string is returned, even though we expect it to not return anything

if (error) {
  console.log(error);
}
```

try/catch is build for handling errors gracefully, and make the intention of the block of code clear.

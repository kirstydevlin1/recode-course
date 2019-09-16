## Step 3 - Give your pet a name

So far, our `Pet` constructor just gives us an empty object. It's a start, but it's only halfway to our first feature - a pet with a name.

In this challenge, we are going to adapt the `Pet` function so that our pets can have names.

How would we want this to look? So far we can create a new instance of `Pet` by typing `const pet = new Pet('Fido');` in the Node REPL.

How would you adapt that code to be able to give the pet a name? What would you expect the outcome of that action to be?

Try the following in the Node REPL:

```js
const pet = new Pet('Fido');
pet.name;
```

What value do you get back?

## Learning objectives

- setting properties of objects using constructors
- `this`

##  To complete this challenge, you will need to:
- discuss this outcome with your pair partner:
  - what would you want the outcome to be?
  - how does this differ from what you are seeing?
  - can you suggest a way of solving the problem?
- translate this error into a new unit test - what do you expect to happen when you call `new Pet('fido');`?
- update your `Pet` constructor function to make the test pass

Once you are done, commit your work, and push to GitHub

## Recommended Reading
- [Constructors and Prototypes](http://tobyho.com/2010/11/22/javascript-constructors-and/)
- [this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)

## [Walkthrough](./Walkthrough/step3.md)

## [Step 4](step4.md)

## Step 2 - Defining the Pet constructor

In JavaScript, we can use **constructor functions** to objects of the same type. These objects can be used to model things in the real world.

To create a new **instance** of an object, we use the `new` keyword.

The first feature of our virtual pet is that it should have a name.

In this challenge, we are going to create a `Pet` constructor function that will allow us to create our new pet.

## Learning objectives

- feature testing in the Node REPL
- writing unit tests to describe expected behaviour of a function
- debugging using a stack trace
- exporting things from files using `module.exports`
- requiring exported values using `require`
- writing a constructor function

##  To complete this challenge, you will need to:
- open the Node REPL
- create a new variable `pet` equal to `new Pet('Fido');`
- discuss the resulting error with your pair partner
  - what is the type of error?
  - research what this error type means.
  - can you suggest a way of solving the problem?
- translate this error into a unit test - what do you expect to happen when you call `new Pet('Fido')`?
- create a `Pet` constructor function and export it from the file
- require the `Pet` function into your unit test and make the test pass

Once you are done, commit your work, and push to GitHub:

## Recommended Reading
- [Node REPL](../../bytes/tools/node-cli.md)
- [Jest matchers](https://facebook.github.io/jest/docs/en/expect.html)
- [module.exports and require on FreeCodeCamp](https://medium.freecodecamp.org/requiring-modules-in-node-js-everything-you-need-to-know-e7fbd119be8)

## [Walkthrough](walkthrough/step2.md)

## [Step 3](step3.md)
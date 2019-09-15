### Step 10 - Guard clauses and errors

Now that we have brought mortality to our virtual pets, we need to let them rest in peace.

Your challenge in this step is to add some **guard clauses** to the `walk`, `growUp` and `feed` functions to prevent them from being used if the pet is not alive. We also need to an a new return value to the `checkUp` function.

- if the pet is not alive, the `checkUp` function should return `'Your pet is no longer alive :('`
- if the pet is not alive, the `walk`, `growUp` and `feed` functions should each throw an exception `'Your pet is no longer alive :('`.
- it the pet is alive, they should behave as before.

## Learning objectives
- Adding guard clauses to prevent misuse of a function
- Throwing exceptions
- Errors
- Testing errors

##  To complete this challenge, you will need to:
- test the expected behaviour in the Node CLI
- write unit tests to to cover the expected behaviour
- add guard clauses to the Pet's methods

Once you are done, commit your work, push to GitHub, and then you're done! Congrats!

## Recommended Reading
- [Guard clauses](https://elliotekj.com/2016/12/02/guard-clauses-in-javascript/)
- [throw](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw)
- [JavaScript Errors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)
- [Testing for errors in Jest](https://facebook.github.io/jest/docs/en/expect.html#tothrowerror)

## [Walkthrough](walkthrough/step10.md)

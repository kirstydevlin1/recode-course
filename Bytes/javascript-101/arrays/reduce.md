# Array Iterators - `reduce`

`reduce` has an accumulator, which - every time an element is iterated over - is modified. When iteration of the array has finished, the `reduce` returns the final value of the accumulator. `reduce` passes 4 arguments to your callback function's parameters (in order):

* `accumulator` - the accumulator to modify on each iteration
* `currentValue` - the value of the current element
* `index` - the index of the current element in the given array
* `array` - the array being iterated over (if you've assigned your array to a variable then you usually won't need this parameter)

In addition to the callback function, the `reduce` function has a second parameter of `initialValue`. The argument passed is the starting value of `accumulator` (it defaults to the first element in the array otherwise).

## When to use `reduce`

The most common use case is when calculating totals, but there are many cool things you can do with `reduce`. Check out [How JavaScript’s Reduce method works, when to use it, and some of the cool things it can do](https://medium.freecodecamp.org/reduce-f47a7da511a9) on Free Code Camp.

## Example Scenario

Chelsie has just started University, and needs to budget how much disposable income she'll have left from her maintenance loan a week after expenses. Chelsie's maintenance loan is £200 a week. Note that the example uses pence units, as to prevent any issues that might occur due to decimal precision - read [this article](http://adripofjavascript.com/blog/drips/avoiding-problems-with-decimal-math-in-javascript.html).

### Code

```js
const expenses = [{
  type: 'rent',
  amount: 15000
}, {
  type: 'food',
  amount: 3000
}, {
  type: 'books',
  amount: 1000
}, {
  type: 'laundry',
  amount: 500
}, {
  type: 'travel',
  amount: 1500
}]

const amountRemaining = expenses.reduce((accum, expense) => accum - expense.amount, 20000)
console.log(amountRemaining / 100) // -10
```

## [reduce on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

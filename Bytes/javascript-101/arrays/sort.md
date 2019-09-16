# Array Iterators - `sort`

`sort` will sort elements in an array. It has an optional parameter of `compareFunction`, which determines the sort order. If `compareFunction` isn't provided, then `sort` will convert all elements in the array to strings and compare them in Unicode point order (uppercase letters come before lowercase letters).

The `compareFunction` callback has 2 parameters `a`, and `b`. `a` is the element currently being iterated over, and `b` is the next element in the array. If `compareFunction` returns `0` then their positions in the array will stay the same. If it returns less than `0` then `a` will come before `b`. If it returns greater than `0` then `b` will come before `a`.

`sort` mutates the original array.

## When to use `sort`

Any scenario in which you need to present data in a particular order, or run a process on data in a particular order.

## Example Scenario

On Amazon, the default product sort order is by relevance to the search term. We can use `sort` on an array of products to sort products by lowest price first.

### Code

```js
const headphones = [{
  name: 'Apple Airpods',
  price: 15000
}, {
  name: 'Sony Headphones',
  price: 5000
}, {
  name: 'Marshall Headphones',
  price: 6000
}]

headphones.sort((headphonesA, headphonesB) => headphonesA.price - headphonesB.price)
console.log(headphones)
// [
//   { name: 'Sony Headphones', price: 5000 }, 
//   { name: 'Marshall Headphones', price: 6000 }
//   { name: 'Apple Airpods', price: 15000 }, 
// ]
```

If `headphonesA` is the object for `Apple Airpods` and `headphonesB` is the object for `Sony Headphones` then the `compareFunction` formula will be `15000 - 5000` which equals `10000`. `10000` is greater than `0` so `headphonesB` gets moved in front of `headphonesA` in the array.

## [sort on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

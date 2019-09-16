# Array Iterators - `filter`

The `.filter` method iterates over each element in an array, calling a callback function you provide. If your callback function returns `true` then the current element being iterated over gets added to a new array (`filter` doesn't mutate the original array). 3 arguments get passed to your callback function:

* `currentValue` - the value of the current element
* `index` - the index of the current element in the given array
* `array` - the array being iterated over (if you've assigned your array to a variable then you usually won't need this parameter)

## When to use `filter`

`filter` is great for when you want to create a new array of elements (from another array) where all of the elements have met a condition you've set. 

## Example Scenario

You're shopping for a laptop on eBay, and you're only interested in laptops running Windows XP. You could use `filter`, and pass a callback function that returns `true` if the `currentValue` (current laptop being iterated over) has an `operatingSystem` property with a value of `Windows XP`.

### Code

```js
const laptops = [{
  model: 'Dell Inspiron',
  operatingSystem: 'Windows XP',
  price: 1250
}, {
  model: 'Microsoft Surface Pro',
  operatingSystem: 'Windows 10',
  price: 800
}, {
  model: 'Lenovo Thinkpad',
  operatingSystem: 'Ubuntu',
  price: 250
}, {
  model: 'Toshiba Satellite',
  operatingSystem: 'Windows XP',
  price: 400
}]

const windowsXPLaptops = laptops.filter(laptop => {
  laptop.operatingSystem === 'Windows XP'
})
console.log(laptops)
// [
//   { model: 'Dell Inspiron', operatingSystem: 'Windows XP', price: 1250 },
//   { model: 'Toshiba Satellite', operatingSystem: 'Windows XP', price: 400 }
// ]
```

## [filter on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

# Array Iterators - `map`

The `.map` method iterates over each element in an array, calling a callback function you provide. The return value of this function gets appended to a new array (`map` doesn't mutate the original array). 3 arguments get passed to your callback function:

* `currentValue` - the value of the current element
* `index` - the index of the current element in the given array
* `array` - the array being iterated over (if you've assigned your array to a variable then you usually won't need this parameter)

## When to use `map`

`map` is great for when you want to create a new array of elements where each element has been calculated from (and corresponds to) an element in a different array.

## Example Scenario

A teacher has reports for all of their students. Each report has their name, grade and attendance. Ofsted are inspecting the school and have asked for an anonymised list of grades. We could use a `map` in this scenario to iterate over every `report` in a `reports` array. The callback function we provide will be passed a `report`. We can return `report.grade` from that callback function to create a new array with just grades.

### Code

```js
const reports = [{
  name: 'Jimmy',
  grade: 'B',
  attendance: 96
}, {
  name: 'Thelma',
  grade: 'A',
  attendance: 100
}, {
  name: 'Aimee',
  grade: 'C',
  attendance: 85
}, {
  name: 'Lee',
  grade: 'D',
  attendance: 72
}]

const grades = reports.map(report => report.grade)
console.log(grades) // ['B', 'A', 'C', 'D']
```

## [map on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

# Array Iterators - `find`

The `.find` method iterates over each element in an array until the callback function you provide returns `true` indicating a record has met criteria you've specified. `find` passes 3 arguments to your callback function's parameters (in order):

* `currentValue` - the value of the current element
* `index` - the index of the current element in the given array
* `array` - the array being iterated over (if you've assigned your array to a variable then you usually won't need this parameter)

## When to use `find`

`find` is great when you have a scenario in which you need to retrieve an element from an array and you don't know it's index.

## Example Scenario

A local library has books, each of which has an ISBN. Their online e-library system allows members to search for a book by its ISBN and if there is a book (or many books with the same ISBN) then a member can take one out.  

### Code

```js
const books = [
  { name: 'The Wizard of Oz', isbn: '540290' },
  { name: 'Pride and Prejudice', isbn: '094290' },
  { name: 'Pride and Prejudice', isbn: '094290' },
  { name: 'Harry Potter', isbn: '193375' }
]

const findBookByIsbn = (isbn, books) => {
  return books.find(book => book.isbn === isbn)
}

findBookByIsbn('094290', books)
// { name: 'Pride and Prejudice', isbn: '094290' }
```

(Note: there are two Pride and Prejudice books. The one returned will be the one at index 1 as its the first one found)

## [find on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

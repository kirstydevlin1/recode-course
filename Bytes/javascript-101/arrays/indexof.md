# Array Iterators - `indexOf`

`indexOf` iterates over an array until it finds the given element, at which point it returns the element's index, or `-1` if the element doesn't exist. Unlike other array iterator methods, it doesn't take a callback. It has the following parameters:

* `searchElement` - the element you want to find the index for
* `fromIndex`- the index to start searching from. Defaults to `0` if not specified.

## When to use `indexOf`

Use `indexOf` if you need to find an element's index in order to use other array methods such as [splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) (a.k.a deleting an element from an array), or if you want to ensure you don't push a duplicate item into an array.

## Example Scenario

Sandra collects coins, but her coin book only has a single slot for each coin. Therefore, if we imagine Sandra's coin book as an array, then we have to ensure Sandra can't _push_ the same coin twice.

### Code

```js
const coins = [{
  denomination: 50,
  year: 2012,
  name: 'Olympic 50p'
}, {
  denomination: 200,
  year: 2005,
  name: 'Guy Fawkes £2'
}, {
  denomination: 2,
  year: 1983,
  name: 'New Pence Two Pence'
}]

const addCoin = (coin, coinBook) => {
  const coinExists = coinBook.indexOf(coin)

  if (coinExists !== -1) {
    throw new Error('Coin already exists!')
  }

  coinBook.push(coin)
} 

const sandrasCoinBook = []
addCoin(coins[0], sandrasCoinBook)
addCoin(coins[0], sandrasCoinBook) // Error: Coin already exists!
```

[find](./find.md) could be used instead in the above scenario.

## Example Scenario

Sandra's Mum has found a rare coin that Sandra has been searching for desperately, and rushes over to her house to surprise her. Sandra has already found this coin though. In order to avoid disappointing her Mum, she scrambles over to her coinbook and attempts to find the coin so she can hide it. Given the coin, we need to find it's index so we can _splice_ it from the coinbook.

### Code

```js
const coins = [{
  denomination: 50,
  year: 2012,
  name: 'Olympic 50p'
}, {
  denomination: 200,
  year: 2005,
  name: 'Guy Fawkes £2'
}, {
  denomination: 2,
  year: 1983,
  name: 'New Pence Two Pence'
}]

const removeCoin = (coin, coinBook) => {
  const coinToRemove = coinBook.find(existingCoin => existingCoin.name === coin.name)
  const existingCoinIndex = coinBook.indexOf(coinToRemove)

  return coinBook.splice(existingCoinIndex, 1)
} 

const sandrasCoinBook = [{
  denomination: 50,
  year: 2012,
  name: 'Olympic 50p'
}]

removeCoin({
  denomination: 50,
  year: 2012,
  name: 'Olympic 50p'
}, sandrasCoinBook)
console.log(sandrasCoinBook) // []
```

We use `find` above because objects are unique. Sandra's 50p and her Mum's 50p are both the same rare specification, but they are different coins. In JavaScript, the object we have as an element in `sandrasCoinBook` is different to the object we pass to `removeCoin`. It is recommended for this reason that if you are working with objects in arrays, that you always use `find` in combination with `indexOf`.

## [indexOf on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)

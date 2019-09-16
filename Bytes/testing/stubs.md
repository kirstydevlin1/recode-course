# Stubs

Stubs are a type of test double - slightly more complex than mocks in that they are essentially "fake" objects that having matching properties and/or methods that our real objects would have. As long as the interface (the object's property names and value types) matches then we can successfully use stubs in place of our other objects in order to further isolate our test suites.

Let's look at an example:

```js
function VendingMachine () {
  this.snacks = [];
}

VendingMachine.prototype.addSnack = function addSnack (snack) {
  this.snacks.push(snack)
}

function Snack (name) {
  this.name = name
}

test('snack can be added', () => {
  const vendingMachine = new VendingMachine();
  const snack = { name: 'Caramac Bar' };

  vendingMachine.addSnack(snack);

  expect(vendingMachine.snacks).toContain(snack);
})
```

Assume the `test` method is called inside a separate test file where we only want to test the `VendingMachine` does its job properly. In the `test` method's callback function, we could set the `snack` to `new Snack('Caramac Bar')` but then we don't have an isolated test, as we'd be testing both `VendingMachine` and `Snack`. Instead we can create an object literal, which matches the interface of the `Snack` object a.k.a a _stub_.

We can also create stub objects that match an interfaces methods (and give them the return values required to keep our object under test happy):

```js
function VendingMachine () {
  this.totalPrice = 0;
}

VendingMachine.prototype.purchaseSnack = function purchaseSnack (snack) {
  this.totalPrice += snack.getPrice()
}

function Snack (name, price) {
  this.name = name
  this.price = price
}

Snack.prototype.getPrice = function getPrice (snack) {
  return this.price
}

test('snack can be purchased', () => {
  const vendingMachine = new VendingMachine();
  const snack = { getPrice: () => 0.79 };

  vendingMachine.purchaseSnack(snack);

  expect(vendingMachine.totalPrice).toBe(0.79);
})
```

Here, `vendingMachine.purchaseSnack` calls the `getPrice` method on our stub. It still works as the interface is identical to that of `Snack`.
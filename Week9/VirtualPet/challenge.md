# Optional challenge: Having a baby

You're now going to make it possible for your pet to have children (a Pet object within a Pet). There are 2 ways you might approach this (if you can think of another approach then give it a go and be sure to try both and take time to work out how each one is working!).

Please take time to read the whole page through before getting started, as the feature tests detailed below will likely help to guide you.

## Creating a new Pet and injecting into your Pet instance

For this approach you will use _dependency injection_. This essentially means passing an object into a different object so that the different object can call the passed in object's methods and access its properties.

### Unit Test

You will:

* Make 2 Pet instances - 1 of which will be the child.
* Call a method on the parent pet, which you pass the child into as an argument e.g. `adoptChild`.
* Assert that the parent pet's `children` property is an array, where the first element is the child instance you originally passed to `adoptChild`.

### Code

You should be able to work out your code from the unit test.

### Feature Test

Your feature test in the Node REPL might look something like this:

```js
const Pet = require('./src/pet');

const parent = new Pet('Dave');
const child = new Pet('Amelia');

parent.adoptChild(child);
parent.children // [ Pet { name: 'Amelia', children: [] } ]
```

Note that it's not currently the parent's responsibility to look after their child so you will have another mouth to feed. You can use the `child` variable to look after the Pet, but you could also access it by looking at the parent's children:

```js
parent.children[0].feed()
```

## Creating a new Pet from inside your Pet instance

This is a slightly different approach from the one above. The benefit of the approach above is that the parent object's `children` can contain objects that don't necessarily have to be an instance of `Pet` - you could pass in anything that had the same method/property names! This is generally a good thing in programming as it opens your code up to expansion.

However, in this scenario where we just want to create a new object of the same instance (`Pet`), it would be perfectly acceptable to create the pet from inside another pet (as opposed to passing it in as a method argument).

### Unit Test

You will:

* Make 1 Pet instances - the parent.
* Call a method on the parent pet, which you pass the child's **name** into as an argument e.g. `haveBaby('Amelia')`.
* Assert that the parent pet's `children` property is an array, where the first element is an instance of Pet with a `name` property of `Billy` (2 different assertions).

### Code

Again your test should guide you on this, but it's likely that you will instantiate a new Pet from inside the `haveBaby` method, using the name passed in, and that this new pet will get added to the parent's `children`.

### Feature Test

```js
const Pet = require('./src/pet');

const parent = new Pet('Dave');

parent.haveBaby('Amelia');
parent.children // [ Pet { name: 'Amelia', children: [] } ]
```

# Step 6 - Intro to Testing React Components

Now we have build our component, lets look into how we might test it.

Testing React - and testing a UI in general - is a little different to the plain JavaScript testing we've seen before. This is because we need the components to be rendered somewhere in order to check how they work, and also how they look.

There are a number of options available - we could boot up a browser and click around manually. We could automate the clicking around in a browser. Both of these options are a little slow, and automated browser testing is notoriously tricky to set up.

Jest gives us the option of snapshot testing - when your tests run, it will take snapshots of your components and compare them to the last time you successfully ran the tests. You can visually see what the component looks like on the page, and it highlights any changes or problems.

This is a good option, but we are just going to look into testing how our components **behave**.

To do this, we can use a library called **Enzyme**, which is an open-source test renderer made by AirBnB. It allows us to render our components into a virtual DOM, and gives us some helper methods that help to make assertions about what is being rendered, and help us interact with the component by simulating clicks etc.

Using Enzyme means we don't have to open a browser to test our components. Again, the component gets rendered into a virtual DOM provided by Enzyme, and we can then make assertions about the state of that DOM.

It's important to note that Enzyme is not a test framework by itself, it is just a testing tool, so we need to use it in conjunction with Jest.

To get started, first create a new directory `__tests__/components` and a new file in that directory `location-details.test.jsx`.

Because we're testing our components, we need to use JSX, and so we need to import React into the test. We also need to import Enzyme in order to use that, and also import the component that we want to test:

```js
import React from 'react';
import Enzyme from 'enzyme';
import LocationDetails from '../../src/components/location-details';
```

**N.B.** you would normally have to install Enzyme as a dev dependency using npm, but we have included it in the React bootstrap repo by default.

Now think about the behaviour of our component - what does it do? It's pretty simple - it takes a city and a country, and renders them inside of a `h1` tag.

So we can start by translating that to a Jest test:

```js
it('renders the passed city and country in a h1 tag', () => {

});
```

To test this, we need to render the component using Enzyme. We can pass props like normal:

```jsx
it('renders the passed city and country in a h1 tag', () => {
  const wrapper = Enzyme.shallow((
    <LocationDetails city="foo" country="bar" />
  ));
});
```

This creates a variable `wrapper` in the test, which is the rendered component.

This rendered component gives us some utility methods to find information about it. These include `find`, which takes a CSS selector, and returns the matching elements inside the component.

Once you have selected an element using `find`, you can use the `text` method to
get the text from the element.


To get the text from the h1 element inside of the rendered component, we can do the following:

```jsx
it('renders the passed city and country in a h1 tag', () => {
  const wrapper = Enzyme.shallow((
    <LocationDetails city="foo" country="bar" />
  ));

  const text = wrapper.find('h1').text();
});
```

Here, we found the element by it's tag - `'h1'`, but we can also search for `.className` or `#id`, just like in CSS.

Now that we have the text, we can just make a normal Jest assertion to check that it is what we expected it to be:

```jsx
it('renders the passed city and country in a h1 tag', () => {
  const wrapper = Enzyme.shallow((
    <LocationDetails city="foo" country="bar" />
  ));

  const text = wrapper.find('h1').text();

  expect(text).toEqual('foo, bar');
});
```

If you run `npm test`, you should now have a passing test. Nice work. Make sure you understand what's going on, maybe take a look at the [enzyme docs](http://airbnb.io/enzyme/docs/api/shallow.html).

## [Next Step: Making the Summary Component](step-7.md)

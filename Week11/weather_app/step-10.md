# Step 10 - Testing rendered components

In the previous tests we have written, we have been testing components that only render basic elements. However, the `ForecastSummaries` component we have written doesn't do this - it renders a component (`ForecastSummary`).

Beyond this, it actually renders the component multiple times.

The behaviour we want to verify here then is
- the component renders the `ForecastSummary` component the correct number of times.
- each iteration of `ForecastSummary` gets passed the correct props.

In order to make assertions about `ForecastSummary` components inside of `ForecastSummaries` we can actually pass the component constructor function into enzyme's `find` method:

```jsx
import React from 'react';
import Enzyme from 'enzyme';
import ForecastSummaries from '../../src/components/forecast-summaries';
import ForecastSummary from '../../src/components/forecast-summary';

const forecasts = [
  {
    date: 123,
    description: 'date1',
    icon: 'icon1',
    temperature: {
      max: 999,
    },
  },
  {
    date: 456,
    description: 'date2',
    icon: 'icon2',
    temperature: {
      max: 777,
    },
  },
];

it('renders the correct amount of ForecastSummary components', () => {
  const wrapper = Enzyme.shallow((
    <ForecastSummaries forecasts={forecasts} />
  ));

  expect(wrapper.find(ForecastSummary).length).toEqual(2);
});
```

Here, we are making an array of mock forecast objects, which have the same shape we expect in the PropTypes for `ForecastSummaries`. In the test, we pass this array into the `ForecastSummaries` component, and render it with Enzyme's shallow render.

We then use the `find` method on the returned wrapper to find all of the `ForecastSummary` components that have been rendered.

`find` returns an array, so we are just asserting that the correct number of `ForecastSummary` components have been rendered.

Now try and write a test that asserts that each Component receives the correct props.

You can use the **prop** and **forEach** methods from Enzyme to help you. (Be careful to use **prop**, and not **props**)

## Recommended Reading

* [Enzyme documentation: `prop` method](http://airbnb.io/enzyme/docs/api/ShallowWrapper/prop.html)
* [Enzyme documentation: `props` method](http://airbnb.io/enzyme/docs/api/ShallowWrapper/props.html)
* [Enzyme documentation: `forEach` method](http://airbnb.io/enzyme/docs/api/ShallowWrapper/forEach.html)

## [Walkthrough](solutions/step-10.md)
## [Next Step: Formatting the icons and date](step-11.md)

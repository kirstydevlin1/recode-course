# Step 8 - Making Lists

We now have a single summary component. The next step of the feature we are working on is to repeat this component for each day of our forecast.

Take a look at the annotated mockup of the app we are trying to create:

![App](images/annotated-app.png "App")

The component we just made corresponds to the yellow boxes. If the whole picture represents our App component, you'll notice that the App directly contains three components (red, blue, green) - the yellow boxes are contained within the blue component.

In this challenge, we are going to make a component which does exactly that - it will be rendered inside of our `App` component, take the forecast list data as props, and it will use that list to render a `ForecastSummary` component for each item in the array.

First up, lets do some plumbing - we have the top level `App` and we have the bottom level `ForecastSummary` - but the `ForecastSummary` is not being rendered anywhere - we want to connect them via this component, so let's just create *SOMETHING* that can be rendered from the `App` component. Then as we build, we will be able to see our work in the browser.

Create a file `src/components/forecast-summaries.jsx` and add some skeleton code:

```jsx
import React from 'react';

const ForecastSummaries = props => (
  <div className="forecast-summaries"></div>
);

export default ForecastSummaries;
```

Next, import this file into `App`, and render it below the `LocationDetails` component:

```jsx
import React from 'react';
import PropTypes from 'prop-types';

import LocationDetails from './location-details';
import ForecastSummaries from './forecast-summaries';

const App = props => (
  <div className="forecast">
    <LocationDetails
      city={props.location.city}
      country={props.location.country}
    />
    <ForecastSummaries />
  </div>
);
```

If you look in your browser devtools now, you should see the forecast summaries component being rendered in the DOM.

Next, we wanted to use the list of forecasts in the `ForecastSummaries` component - but where does that data come from? It comes from `App`. And where does `App` get it from? It receives it as props when we initially render it in `index.jsx`

So firstly, we need to import the forecasts data from the JSON file in `index.jsx` and pass it into `App` as a `forecasts` props:

```jsx
import { location, forecasts } from './data/forecast.json';

render(<App location={location} forecasts={forecasts} />, document.getElementById('root'));
```

Now you have the data available to you in `App`'s props. We need to add this to `App`'s proptypes:

```js
App.propTypes = {
  location: PropTypes.shape({
    city: PropTypes.string,
    country: PropTypes.string,
  }).isRequired,
  forecasts: PropTypes.array.isRequired,
};
```

Finally, we need to pass the list of forecasts into the `ForecastSummaries` component as props.

```jsx
const App = props => (
  <div className="forecast">
    <LocationDetails
      city={props.location.city}
      country={props.location.country}
    />
    <ForecastSummaries forecasts={props.forecasts} />
  </div>
);
```

And now the plumbing is done - we are rendering the `ForecastSummaries` from `App`, and passing in the right data. Now we just need to build the `ForecastSummaries` component so it meets our requirements.

Inside of the `ForecastSummaries`, we are going to use `Array.map` on the forecasts array, to transform each forecast into a `ForecastSummary` component.

```jsx
import React from 'react';

import ForecastSummary from './forecast-summary';

const ForecastSummaries = props => (
  <div className="forecast-summaries">
    {
      props.forecasts.map(forecast => (
        <ForecastSummary
          date={forecast.date}
          description={forecast.description}
          icon={forecast.icon}
          temperature={forecast.temperature.max}
        />
      ))
    }
  </div>
);

export default ForecastSummaries;
```

If you look in your browser, you should now see the summary component being rendered for each day. That was easy, wasn't it? It might look a bit weird (i.e. stacked vertically) - we will look at adding some CSS in the next step.

Because we are now using the `forecasts` prop, we should add it to PropTypes - can you do that?

A final thing with this step - if you look in the browser console, you should see a warning:

```
Each child in an array or iterator should have a unique "key" prop.
```

You can read about this error here: [Lists & Keys in React](https://reactjs.org/docs/lists-and-keys.html#keys) (that whole doc is worth a read actually...)

React works in a way where it only tries to make the changes to the DOM that are necessary. When we use `map` to render a list of components, and an item gets added or removed from the array, it is more efficient for React to only update the item that has been added or removed, rather than re-rendering the full array. Similarly, if the array is re-ordered, it is more efficient to only update the items that have moved position.

Because of this, it helps React to pass in a `key` prop to the component that is being rendered in the iterator (in our case `ForecastSummary`), which helps React more easily identify which element is which.

There are a couple of rules for what values these keys should have:
- They should be unique to that item - if two items have the same key, React will only render the component for the first item. So if you are rendering a list of people, don't use the first name as a key, as there may be more than one Joe in your list, but only the first Joe will be rendered.
- The key should not be the array index - this is the most tempting option for what to pass as a key - the first item in the list has key 0, the second item in the list has key 1 etc. But what happens if you add a new item to the middle of the list, so item 5 becomes item 6 etc. Or if you shuffle the items around? Doing this can cause React to get confused, so try to avoid it, especially if it's possible that your array might change.

With this in mind, can you see a property of each forecast which might be unique to the individual forecast? I would say that the date is a good candidate. So lets pass this into the `ForecastSummary` as the `key` prop:

```jsx
const ForecastSummaries = props => (
  <div className="forecast-summaries">
    {
      props.forecasts.map(forecast => (
        <ForecastSummary
          key={forecast.date}
          date={forecast.date}
          description={forecast.description}
          icon={forecast.icon}
          temperature={forecast.temperature.max}
        />
      ))
    }
  </div>
);
```

The console warning should now be gone - lets move on and look at applying some styles to our components.

## [Next Step: CSS in React](step-9.md)

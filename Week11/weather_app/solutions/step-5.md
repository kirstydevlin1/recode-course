# Step 5 - Solution

Following the instructions given in the step 5, you should now have an `index.jsx` file that looks like this:

```jsx
import 'raf/polyfill';
import React from 'react';
import { render } from 'react-dom';

import App from './components/app';

import { location } from './data/forecast.json';

render(<App location={location} />, document.getElementById('root'));
```
The first step in the challenge is to create a file `src/components/location-details.jsx`.

Once you've done that, you need to actually create the component inside of there.

Firstly, you will need to import React into the file - this is done in the same way we've already seen in the other files - `import React from 'react';` at the top of the file.

Remember, that a React component is just a JavaScript function, which receives `props`, and returns some JSX. In our case, we want to render a `<h1>` element.

That should give you something like this:

```jsx
const LocationDetails = () => <h1 className="location-details" />;
```

Note that this element is self-closing (as opposed to having an opening and closing tag, like `<h1></h1>`). In React, if an element has no child elements, it should be self-closing.

In our component design, we said this component would take 2 props - `city` and `country`. We want to render these inside of the component:

```jsx
const LocationDetails = props => <h1 className="location-details">{props.city}, {props.country}</h1>;
```

You should now be seeing a linting error telling you that `city` and `country` are missing from props validation.

To fix this, we need to add prop types.

First, import the prop-types library:

```js
import PropTypes from 'prop-types';
```

Then at the bottom of the file, you need to define what the props for `LocationDetails` should look like. In our case, we have `city` and `country` props, which are both strings. I would also say that they are required for the component to work.

```js
LocationDetails.propTypes = {
  city: PropTypes.string.isRequired,
  country: PropTypes.string.isRequired,
};
```

Finally, you need to export the `LocationDetails` component from the file. At the very bottom of the file, add the following:

```js
export default LocationDetails
```

Now you are ready to use your component in your App component.

To do this, you need to import it into `app.jsx`:

After the other imports in that file, add the line:

```js
import LocationDetails from './location-details';
```

then change App to look like this:

```jsx
const App = () => <LocationDetails />
```

If you check your app in your browser, you should see...nothing! But if you check the DOM in dev tools, you should see that your `h1` element HAS been rendered. If you then check the console tab, you should see a warning from prop types, saying that city and country were expected, but not passed.


To fix this, we need to pass those props in from `App`. The data we want to pass in is the location data from the JSON file, and we have made that available to `App` as the `location` prop.

So, using the props on `App`, we can pass that data into `LocationDetails`:

```jsx
const App = props => <LocationDetails city={props.location.city} country={props.location.country} />;
```

With JSX if our props start to get quite long like this, it is possible to split it onto multiple lines for improved readability:

```jsx
const App = props => (
  <LocationDetails
    city={props.location.city}
    country={props.location.country}
  />
);
```
At the moment, it might seem pretty pointless to have the app structured like this - just rendering a single component - but as the app grows, it will become more apparent why we are structuring it this way. The App component will act as a layout, and a central place for managing our application data. It delegates responsibility for displaying that data to the other components.

The last step in this challenge is to add the `location` prop to the `App` components prop types. Because `location` is an object, we can use `PropTypes.shape` for this:

```js
App.propTypes = {
  location: PropTypes.shape({
    city: PropTypes.string,
    country: PropTypes.string,
  }).isRequired,
};
```

Once you've done that, you are done! Check the browser, and you should see the city details being rendered - if you update them in the json file, it should update in the browser.

## [Next Step: Intro to Testing React Components](../step-6.md)

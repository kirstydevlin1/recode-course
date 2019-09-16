## Props

Because our React components are functions, they can receive parameters. In React terms, these parameters are called **props**

These get passed into the component in the same way you would set a property on an element. Try the following example:

```jsx
render(<App name="Michael" />, document.getElementById('root'));
```

The string "Michael" would then be available to us in the component as a property on the `props` parameter:

```jsx
const App = props => <h1>{`Hello ${props.name}`}</h1>;
```

We use props to make our components more re-usable, and they allow us to control how our components get rendered. Instead of hard-coding the string "World" into `App`, by passing a prop, we can control what gets rendered.

If you change the value of the "name" prop in `index.jsx`, you should see it change in the browser.

Using props, we can make more generic components, which can be configured by passing in props from the parent context. Props is short for properties, but I always imagined it like theatre props.

## PropTypes

Hopefully you noticed that by adding props into the component, you triggered a linting error `react/prop-types`

With React components, you can use the `prop-types` library to tell React what type of thing each prop should be (String, Number etc), and whether that prop is required or optional. It's a little like a schema in mongoose.

Keeping a record of this is useful because it helps other developers who are using your components know exactly how it should be used, as a sort of documentation.

It is also useful because if you pass the wrong type of prop, or if you don't pass in a prop which is marked as required, it will bring up a big red error message in the browser developer console, so you know there could potential be a problem with your app.

By far the most useful reason for using PropTypes, however, is setting default props. This means that if your component expects 10 props, you might actually only need to pass in 3, instead of passing in 10 every time - if you don't pass a prop, it will use the default value instead.

We can set the PropTypes on our component as follows:

```
import React from 'react';
import PropTypes from 'prop-types';

const App = props => <h1>{`Hello ${props.name}!`}</h1>;

App.propTypes = {
  name: PropTypes.string,
};

App.defaultProps = {
  name: 'World',
};

export default App;
```

Experiment with this a little:

- Do not pass a `name` prop in `index.jsx` - notice how it uses the default prop?
- Pass a number instead of a string (`name={9}`) - can you see a warning in the browser console?
- What if you write the above as `name="9"` instead? This time, there should be no prop type warning - can you explain why not? What is the difference between `name={9}` and `name="9"`?
- Remove the `App.defaultProps` object, and add `.isRequired` to the end of `PropTypes.string`. If you don't pass a prop now, can you see a different warning in the browser console?

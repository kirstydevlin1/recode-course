## Components

This byte assumes you have [our React boilerplate](https://github.com/MCRcodes/react-bootstrap) cloned down.

Elements are the most granular building blocks in React. However, the main building blocks in React are called **components**.

A component is most simply described as a part of a user interface. In React, instead of building an entire page, we break the page and the entire application down into smaller, reusable pieces, and think about them in isolation.

In practice, a component is a JavaScript function, which returns a React element.

Lets turn the current Hello World element in the boilerplate into a component.

First create a new file `src/components/app.jsx`, and enter the following code:

```jsx
import React from 'react';

const App = () => <h1>Hello World</h1>;

export default App;
```

This is our first React component.

N.B. the `export default` statement is just a newer version of `module.exports`

The juicy part here is the line `const App = () => <h1>Hello World</h1>;`

As we said, this is a function, which returns a React element.

## Rendering Components

We can render components in React using JSX, just like we can with any element.

Update your `src/index.js` file, so it looks like this:

```jsx
import 'raf/polyfill';
import React from 'react';
import { render } from 'react-dom';
import App from './components/app';

render(<App />, document.getElementById('root'));
```

Here, instead of rendering the plain React element, we are rendering the `App` component.

By convention - elements (`div`, `h1` etc.) are all lowercase, whereas React components begin with a capital letter (`App` instead of `app`).

Being able to render and use components in this way is the great power of React. We can go and update the `App` component in any way we like, without having to change it at this top level.

Additionally, we could render different components inside of our `App` component, so it might look something like this (this is an example - it won't work as you don't have the actual components):

```jsx
const App = () => (
  <div className="app">
    <NavBar />
    <SideBar />
    <Articles />
    <Footer />
  </div>
);
```

Each of the sub-components in App could also be made up of smaller components. Working in this way makes our code cleaner and more focussed - each component can have a clearly defined responsibility - and it also allows you to re-use code. Assume you were making a website with lots of lists - you could create a single `<List />` component, and reuse the same markup throughout the site, without having to repeat yourself. Any changes you wanted to make to how the list looks or functions would be done from a central place.

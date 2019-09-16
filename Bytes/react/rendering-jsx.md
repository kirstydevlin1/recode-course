# Rendering JSX

This byte assumes you have [our React boilerplate](https://github.com/MCRcodes/react-bootstrap) cloned down.

Inside the boilerplate project, take a look at `src/index.jsx` - notice we use the file extension `.jsx` rather than the usual `.js`

This file is the entry point of our app - everything else that goes on will happen via this one.

At the top we have a few `import` statements - `import` is just a more modern version of `require`, so `import React from 'react';` is effectively the same as `const React = require('react');`

Since we are using Babel now, we can use the more modern syntax. We will be doing so, because it's good to get used to these things.

Whenever you are writing React code, you need to import the React library at the top of the file in this way.

## JSX

Now take a look at this code in `index.jsx`:

```html
<h1>Hello World!</h1>
```

This looks like HTML, but it isn't - it is actually JavaScript. More accurately, it is JSX, which is a syntax extention to JavaScript.

JSX produces **React elements**, which describe what you want to see on the screen. Elements are the smallest building blocks of React.

In HTML, we can set properties on elements. In React, we can do the same on elements - these work the same way as normal, the notable exception being that you have to use `className` instead of `class` to set the class attribute.

```html
<h1 className="header">Hello World</h1>
```

Anything which sits between two element tags will be rendered to the DOM as text.

If you look again at the browser, you'll see that's exactly what has happened.

You can also embed any JavaScript expression inside of JSX tags using curly braces.

If you change the code to the following:

```html
<h1>{2 + 2}</h1>
```

Then you should see `4` being rendered to the screen, rather than the old `Hello World!` This is because the expression gets evaluated before the React element gets rendered.

What do you think will happen if you change the code to:

```html
<h1>2 + 2</h1>
```

Can you explain why?

## Rendering

We use the `render` function which we imported from `react-dom` to make our React element appear in the DOM.

```jsx
render(<h1>Hello World!</h1>, document.getElementById('root'));
```

If you look at the `index.html` file, you will see the following:

```html
<div id="root"></div>
<script type="text/javascript" src="app.js"></script>
```

First, note the `<script>` tag, which loads in a JavaScript file called `app.js`. This file contains the code for our application (this is what we have told webpack to call our bundled code).

Second, we have a `<div>` tag with an `id="root"` attribute.

Going back to our `index.jsx` file, this matches with the second argument we have passed to the `render` function - `document.getElementById('root')`. If you cast your minds back a few weeks to when we studied the DOM, we used the `getElementById` function to select a particular DOM node. Here, we are selecting the `id="root"` node, and telling `react-dom` to render our element into that node.

If you take a look in your browser dev tools at the HTML markup that has been rendered, then you will see that your `<h1>Hello World!</h1>` has been rendered as the first child of the `root` node.

Everything that happens in your app will happen inside of this root node.

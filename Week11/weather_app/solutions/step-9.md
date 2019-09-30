# Step 9 - Walkthrough

You should end up with two stylesheets in your `styles` directory:

- `app.scss`:
```css
.forecast {
  font-family: Arial, Helvetica, sans-serif;
  margin: 0 20px;
}
```

- `forecast-summaries.scss`:
```css
.forecast-summaries {
  display: flex;
  justify-content: space-between;
}
```

In `App` and `ForecastSummaries` respectively, you can include these by adding the lines `import '../styles/app.scss;` and `import '../styles/forecast-summaries.scss;`

The `webpack-config` file is (as you can probably guess) - our config file for Webpack - when we run Webpack to build our code, this file defines how Webpack will approach that transformation.

If you look at the `package.json` file, you will see that the `npm start` command is actually aliased to run `webpack-dev-server`. This is a tool which builds our code using Webpack (and our webpack config), and serves it to us on port 8080. So our code is being build with Webpack.

Out of the box, Webpack can only deal with JavaScript and JSON code. If we want to include css, images, or any other type of file in our React applications, we need to add a **loader** to our `webpack.config.js` file.

Loaders work by transforming the file into JavaScript code, which Webpack can understand (we don't have to worry about this too much, thankfully).

In our webpack config, we have the following code:

```js
{
  test: /\.s?css$/,
  use: [{
    loader: 'style-loader',
  }, {
    loader: 'css-loader',
  }, {
    loader: 'sass-loader',
  }],
}
```

The `test` property is a regular expression hich says to Webpack, "when you come across a file in an `import/require` statement which resolves to a file ending in `.css` or `.scss`, use the following loaders to handle that file"

The items in the `use` array define the loaders we want to use, and they form a pipeline, which (confusingly) gets applied in reverse order. In our case we are using
- `sass-loader`, which transforms sass and scss files into normal css
- `css-loader`, which handles css files
- `style-loader`, which transforms css into `style` html tags in the DOM.

Don't worry if this is a bit confusing - the main point here is just to understand that we can load different types of files - images, fonts, stylesheets, anything really - into our JavaScript directly. And if you want/need to do that, then a webpack loader is what you'll need.

## [Next Step: Testing rendered components](../step-10.md)

# React Project Tools

This byte tries to explain at a high level what goes on behind the scenes when you run `npm start` in a React application. If it doesn't make a lot of sense, don't worry. It's mainly here as a reference to help you get unstuck, if you need it at any point.

Take a look at the dependencies and dev dependencies inside the `package.json` file in your React project (you should hopefully have [our boilerplate](https://github.com/MCRcodes/react-bootstrap) cloned down if you are reading this). Lets take a look at the dependencies first. Don't worry if this doesn't all sink in - but remember that this list is here if you need to come back to it at some point.

## Dependencies

```json
"dependencies": {
  "react": "^16.3.2",
  "react-dom": "^16.3.2",
  "prop-types": "^15.6.1",
  "raf": "^3.4.0"
},
```

- *React* - hopefully it's obvious, but this is the React library. You can't write React without it.
- *React DOM* - this allows you to render React to the DOM. It's seperate because you don't have to render React to the DOM (e.g. you can also create mobile apps using React Native)
- *Prop Types* - this is actually used to help you as a developer. It allows you to tell React what sort of values (strings, numbers etc.) you want to pass into the functions, and it will complain if you pass the wrong type of thing. It's useful and makes you think.
- *RAF* - `requestAnimationFrame` - this helps React to work in some browsers, it's good practice to install it with version 16 of React, but it's not something you need to worry too much about.

## Dev Dependencies

```json
"devDependencies": {
  "babel-jest": "^22.4.3",
  "babel-loader": "^7.1.4",
  "babel-preset-env": "^1.6.1",
  "babel-preset-react": "^6.24.1",
  "css-loader": "^0.28.11",
  "enzyme": "^3.3.0",
  "enzyme-adapter-react-16": "^1.1.1",
  "eslint": "^4.19.1",
  "eslint-config-airbnb": "^16.1.0",
  "eslint-plugin-import": "^2.11.0",
  "eslint-plugin-jsx-a11y": "^6.0.3",
  "eslint-plugin-react": "^7.7.0",
  "file-loader": "^1.1.11",
  "jest": "^22.4.3",
  "node-sass": "^4.9.0",
  "react-test-renderer": "^16.3.2",
  "sass-loader": "^7.0.1",
  "style-loader": "^0.21.0",
  "webpack": "^4.6.0",
  "webpack-cli": "^2.0.15",
  "webpack-dev-server": "^3.1.3"
}
```

Outside of Jest and ESLint, these can be grouped into roughly 3:

- *Babel* - this is a compiler. Behind the scenes, React is JavaScript. However, it utilises a syntax called **JSX** which is a hybrid between HTML and JavaScript - JSX syntax isn't actually valid JavaScript, so Babel will transform it to normal JavaScript for us.  Again, don't worry about this too much. `babel-loader` tells webpack to use babel when it bundles our code, so it all happens seamlessly, as we will see.
- *Enzyme* - this is something that helps you test React code - we'll see it more shortly. `react-test-renderer` is required for Enzyme to work.
- *Webpack* -  our React apps will be made up of lots of files, but because it runs in the browser, we need to download those files - Webpack is a *module bundler* that basically takes all of your files, and puts them into one file, which is much easier to download. It's really powerful, really configurable, and also quite confusing, so don't worry about it too much. We will only go into it when we need to. The exciting thing here is `webpack-dev-server`, which is like `nodemon` for the browser - when you save your code, it will automatically rebuild it and refresh the browser tab for you. `node-sass` and everything ending in `loader` are required to load css, images, fonts etc into webpack.

Now that you have some idea about what those things are (again, don't worry if things don't make sense now, keep coming back and reading over!), lets actually get started...

- run `npm start` - this will run the `start` script defined in `package.json`, which you will see runs `webpack-dev-server`. `npm start` will kick off Webpack, which will transform all of our code using Babel, then transform it into a single file, and then make our React app available to us on `localhost:8080` - if you go to that URL in your browser, you should see your React application running.

Again **DON'T let this overwhelm you** - all you have to do for now is run `npm start`, and you have a working React application.

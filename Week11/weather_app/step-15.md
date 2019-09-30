# Step 15 - Fetching external data - Lifecycle methods

The first iteration of the App is now pretty much complete. However, we are still only displaying the static data defined in the `forecast.json` file. It would be much cooler if we could make the app display real weather data. In this step, that's exactly what we're going to do.

To help with this, we have created a web API for you to use, at [mcr-codes-weather.herokuapp.com](https://mcr-codes-weather.herokuapp.com).

Take a look at the API documentation provided (click the link above). Using Postman, you should be able to make a HTTP request to retrieve some live weather data from the API - give it a go!

## Component Lifecycle

While our App is running, the components that make up the App can go through various changes.
All of the components that appear in the DOM don't appear by magic, they go through a process of being created and rendered. Once they are rendered, we might want to update them when the state or props change. Sometimes, we might want to remove a component from the DOM.

These three categories of events (creation (**mounting** in React language), **updating** and removal (a.k.a. **unmounting**)) make up what is known as the **component lifecycle**

When we use class components, we have access to **lifecycle methods**, which we can use to control what happens at each stage of the components lifecycle.

The main lifecycle methods we have to worry about are:

* `constructor`
* `componentWillMount`
* `render`
* `componentDidMount`
* `componentWillReceiveProps`
* `shouldComponentUpdate`
* `componentWillUpdate`
* `componentDidUpdate`
* `componentWillUnmount`

When a component mounts, the `constructor`, `componentWillMount`, `render` and `componentDidMount` methods will be called in that order.

When a component updates, `componentWillReceiveProps`, `shouldComponentUpdate`, `componentWillUpdate`, `render` and `componentDidUpdate` get called in that order.

When a component will unmount, unsurprisingly it is `componentWillUnmount` that gets called.

We have covered `constructor` and `render` before.

A lot of the time, you don't need to worry about most the lifecycle methods. They should be used sparingly - I have barely ever used `shouldUpdate`, `willUpdate` or `didUpdate`. But it's worth understanding what they are, knowing what methods are available, and understanding what they do.

We are going to use the `componentDidMount` method in our `App` to make a http request using the Axios library to fetch the live weather data.

To complete this step:

- In your `index.jsx` file, remove the imported json file, and remove the props you are passing into `App`
- In your `App` component, add an extra property `forecasts` to your `state` object in the `constructor` metthod. Set this to be an empty array.
- Add a `location` property to state. Set it equal to an object with `city` and `country` properties, which are empty strings.
- Remove all references to `this.props.forecasts` and `this.props.location` - replace them with `this.state.forecasts` and `this.state.location` instead.
- Set `state.selectedDate` to 0 - this is just a default/initial value . The app no longer has any forecasts when it loads (we have to wait for the data to load from the API), so our old approach will not work - the forecast we were referring to will no longer exist.
- Since `App` no longer receives any props, you should also be able to remove the prop type definitions.

One other thing we need to fix is in the `render` method. Looking at the app in the browser, you should hopefully see an error message similar to this:

```
Uncaught TypeError: Cannot read property 'date' of undefined
    at ForecastDetails (forecast-details.jsx)
```

As well as a more useful PropType warning (this is one reason why PropTypes are useful):

```
Warning: Failed prop type: The prop `forecast` is marked as required in `ForecastDetails`, but its value is `undefined`.
    in ForecastDetails (created by App)
    in App
```

Our `ForecastSummary` component is expecting a forecast to be passed in. We are selecting that forecast using the following line in `render`:

```js
const selectedForecast = this.state.forecasts.find(forecast => forecast.date === this.state.selectedDate);
```

`Array.find` will return either a matching item, or `undefined`. When our app initial mounts and is rendered, we have set the `forecasts` array to be `empty` - this means that `find` will always return `undefined` (since there is nothing to find), and so we will always be passing `undefined` into our `ForecastSummary` component. Looking back at the error messages, can you that that is what it is telling us?

To fix this, we can use [**conditional rendering**](https://reactjs.org/docs/conditional-rendering.html). This allows us to use *if statements*, *ternaries* and *logical operators* to render one thing or another (or nothing at all), based on the state of the component.

In this case, we only want to render the `ForecastSummary` if there is a forecast with the selectedDate.

In your `App` components `render` method, change `<ForecastDetails forecast={selectedForecast} />` to the following:

```jsx
{
  selectedForecast && <ForecastDetails forecast={selectedForecast} />
}
```

Because we are using actual JavaScript, not just JSX, we have to wrap this block in curly braces. We are then leveraging the truthiness/falsiness of `selectedForecast` in combination with the `&&` operator to conditionally render the `ForecastSummary` component. If `selectedForecast` is `undefined`, then the statement will evaluate to `undefined`, and React will not render anything.
If `selectedForecast` is a truthy value (which it will be if it is a forecast object), then the statement will evaluate to return the RHS of the statement, and the `ForecastSummary` will be rendered.

If you've got this far, then you've successfully re-wired your App, so that instead of reading data from the static JSON file that was passed from outside as props, the data is now completely contained within the local state of the App component. This means that `App` is in charge of it's own data.

To fetch data from the API:

- Use npm to install the `axios` library, and import this into your `App` component
- Add a `componentDidMount` method to your `App` component
- In `componentDidMount`, use `axios` to make a HTTP request for some weather data from the above API
- When the data is returned, use the `setState` method to set the values of `this.state.forecasts` and `this.state.location` appropriately.

If you managed all that, then congratulations. You should see the live weather data being displayed in your app, instead of the static data from the JSON file.

## Recommended Reading

* [Lifecycle Methods](https://reactjs.org/docs/react-component.html#the-component-lifecycle)
* [How and when to use Lifecycle Methods](https://engineering.musefind.com/react-lifecycle-methods-how-and-when-to-use-them-2111a1b692b1)
* [Conditional Rendering](https://reactjs.org/docs/conditional-rendering.html)
* [Axios Documentation](https://github.com/axios/axios)

## [Next Step: Adding Search Functionality](step-16.md)

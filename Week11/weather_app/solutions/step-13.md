Assuming that `App` currently looks like this:

```jsx
const App = props => (
  <LocationDetails
    city={props.location.city}
    country={props.location.country}
  />
  <ForecastSummaries forecasts={props.forecasts} />
  <ForecastDetails forecast={props.forecasts[0]} />
);
```

 Converting this to be a class component will look something like this:

```jsx
class App extends React.Component {
  render() {
    return (
      <LocationDetails
        city={props.location.city}
        country={props.location.country}
      />
      <ForecastSummaries forecasts={props.forecasts} />
      <ForecastDetails forecast={props.forecasts[0]} />
    );
  }
}
```

Adding in some local state means we need to add a `constructor` method to our class, where we can define `this.state`. We have to set the `selectedDate` property on the state object to the date on the first forecast from `props.forecasts`:

```jsx
class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      selectedDate: this.props.forecasts[0].date,
    };
  }

  render() {
    return (
      <LocationDetails
        city={props.location.city}
        country={props.location.country}
      />
      <ForecastSummaries forecasts={props.forecasts} />
      <ForecastDetails forecast={props.forecasts[0]} />
    );
  }
}
```

Then we want to pass a forecast into ForecastDetails based on the selected date:

```jsx
class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      selectedDate: this.props.forecasts[0].date,
    };
  }

  render() {
    const selectedForecast = this.props.forecasts.find(forecast => forecast.date === this.state.selectedDate);

    return (
      <LocationDetails
        city={props.location.city}
        country={props.location.country}
      />
      <ForecastSummaries forecasts={props.forecasts} />
      <ForecastDetails forecast={selectedForecast} />
    );
  }
}
```

Now the `ForecastDetails` component will render whichever forecast matches our selected date. If that date changes, then the forecast rendered in `ForecastDetails` will also change...

## [Next Step: Modifying State & Event Handlers](../step-14.md)

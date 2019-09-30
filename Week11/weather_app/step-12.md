# Step 12 - Detailed forecast component

The last feature we need to implement for our MVP Weather App is:

**Users should be able to click on one of the summaries to view all of the forecasted information for that date**

To start with this feature, we need to create a component which shows the full forecast information for a day.

To complete this step:

- Create a component `ForecastDetails` which takes a single prop `forecast` (this should be an object, where the expected shape is the same as a single item from the forecasts array)
- Make the `ForecastDetails` render the formatted date, the min and max temperatures, the humidity and the wind speed and direction.
- In the `App` component, render this component underneath `ForecastSummaries` - for now, just give it the first forecast from the list (`forecasts[0]`) as a prop.

## [Next Step: Stateful components](step-13.md)

# Step 7 - Making the Summary Component

The requirements for the next feature of our app are:

**_Users should be able to see a summary of each day of the forecast, including the date, general description and an icon for the weather that day, and maximum temperature._**

This can be broken into two problems:
* We need to render the date, description, icon and max temperature for a day.
* We need to repeat this for each day of the forecast.

In this step we are going to solve the first of these problems. Your challenge is to make a component which displays the forecast summary for an individual day.

This is the `ForecastSummary` component we came up with in step 4.

Back then, we said that this component would take 4 props - `date`, `temperature`, `description` and `icon`.

Your challenge in this to create a component which renders these 4 pieces of information.

As usual, you should try doing this test first.

For now, don't worry about displaying the actual icon image or formatting the date, just render the `icon` prop and `date` props as the come. We will get onto making these look prettier shortly.

You should also not worry about "plugging in" the component - for now, the only code you need to write is in `forecast-summary.jsx` and `forecast-summary.test.jsx`. This component belongs in a list, which we will cover in the next step.

As guidance, each prop should be rendered inside of a `span`, and each `span` should be wrapped in a `div`. Add classNames to these `div`s to help you select the elements in your tests.

This step is really similar to the work you did in `location-summary.jsx` in the last step, so if you get stuck, go back to there.

## [Walkthrough](solutions/step-7.md)
## [Next Step: Making Lists](step-8.md)

# Step 11 - Formatting the icons and date

The application is getting somewhere now, but it still looks a bit odd - it's not exactly clear with the date `1525046400000` and the icon `800` mean, is it?  

As developers, a core part of our jobs is handling and manipulating data. As UI developers, it's our job to handle transforming that data into something more user-friendly.

## Formatting the icons

The weather data we are using comes from the open weather map api. This api provides a list of icons for each weather condition, and every response from the api provides an icon id, which can be trsanslated into an icon. [The icons are available to see here](https://openweathermap.org/weather-conditions).

As you can see, these icons are not that attractive. Thankfully, [somebody else has spent some time making their own icons](http://erikflowers.github.io/weather-icons/), which translate from the icon id's from our API. 

And even better, somebody else has spent some time translating these icons into [an easy-to-use r
React component](https://www.npmjs.com/package/react-icons-weather)

The first part of this challenge is to update the `ForecastSummary` component to render a `WeatherIcon` component, in place of the `span` which currently contains the icon id.

Follow the instructions from the package documentation on the npm website (the link above) for instrutions on how to install and use the package. When setting the `name` prop, remember that the icons we are using come from Open Weather Map.

You'll also need to update the tests for the `ForecastSummary` component to check that the `WeatherIcon` gets rendered with the right props, rather than the icon id text.

## Formatting the date

As we mentioned earlier, the date property on our forecasts are formatted as Unix timestamps in milliseconds - that is, the number of milliseconds since 01/01/1970 00:00:00:0000 UTC (the Unix epoch)  

Storing dates in this form makes a lot of sense - it's a consistent format, independent of timezone differences, and it makes comparing dates as simple as comparing two numbers. Unfortunately, it's less readable to a human than to a computer, so we need to format it correctly in order to be able to use it.

To get a date from a unix timestamp in JavaScript, we can use the `Date` constructor - `new Date(1525046400000)`- however, this returns a `Date` object, which is notoriously difficult to format, and generally not that useful.

N.B. you can generate a unix timestamp from a `Date` using `Date.parse`

Thankfully, some other people have spent their time [making a package called `moment](https://www.npmjs.com/package/moment)`, which makes using dates in JavaScript super easy.

To complete this part of the challenge:
- install `moment` via `npm`, saving the package as a dependency
- import `moment` into your `ForecastSummary` component
- where you are rendering the unformatted timestamp, instead, pass the timestamp into the moment function (e.g. moment(1525046400000))
- use moments `format` method on your new date to display it to the format - `Tue 1st Sept` etc. 
- update your tests to assert that a correctly formatted date is returned

## [Walkthrough](solutions/step-11.md)
## [Next Step: Detailed forecast component](step-12.md)

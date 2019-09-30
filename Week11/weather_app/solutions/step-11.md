# Step 11 - Walkthrough

## Part 1
Once you have installed the package, using the `WeatherIcon` component is just like using any other React component. First we import it into `forecast-summary.jsx`:

```js
import WeatherIcon from `react-icons-weather;
```

and then we render it in place of the current span element:

```jsx
<div className="forecast-summary__icon">
  <WeatherIcon name="owm" iconId={props.icon} />
</div>
```

## Part 2
To use moment, you'll need to install moment with npm, and import it into the file.

Moment provides a wrapper around the built-in `Date` object. To create a `moment` object, you call the `moment` function with the date or timestamp that you want to represent. In our cast, that would be `moment(props.date)`.  (If you call `moment` with no arguments, you will get the current date/time).

To format the date, we can use the format function [with the rules specified in the documentation](https://momentjs.com/docs/#/displaying/format/) to display the date in any format we like.

To get 'Tue 1st Sept' we would pass in the string `'ddd Do MMM'`, so overall, we would have:

```js
<div className="forecast-summary__date">
  <span>{moment(props.date).format('ddd Do MMM')}</span>
</div>
```

Don't forget to update your tests!

## [Next Step: Detailed forecast component](../step-12.md)

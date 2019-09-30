# Step 10 - Walkthrough

The find method will return to us all of the DOM nodes which match the given selector.

We can then use the forEach method to make assertions about each node - in this case, we want to check the value of the `date`, `description`, `icon` and `temperature` props that we are passing.

```js
it('passes the correct values from each forecast into each ForecastSummary', () => {
  const wrapper = Enzyme.shallow((
    <ForecastSummaries forecasts={forecasts} />
  ));

  wrapper.find(ForecastSummary).forEach((node, index) => {
    expect(node.prop('date')).toEqual(forecasts[index].date);
    expect(node.prop('description')).toEqual(forecasts[index].description);
    expect(node.prop('icon')).toEqual(forecasts[index].icon);
    expect(node.prop('temperature')).toEqual(forecasts[index].temperature.max);
  });
});
```

## [Next Step: Formatting the icons and date](../step-11.md)

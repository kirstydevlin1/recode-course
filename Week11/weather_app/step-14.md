# Step 14 - Modifying State & Event Handlers

You now have a stateful App component, and instead of rendering the details of the first forecast, you now render the selected forecast, based on whichever date is stored in the component state.

The problem we have now is that our state is always has the selected date from the first forecast, and we cannot update it.

In this step, we are going to update the application state to change the selected date, and be able to render the full forecast details for any date we choose.

The mechanism for selecting the date will be a button on the `ForecastSumary` component. Remember, we are rendering this component for each day of the forecast, so we will end up with a button for each day. Clicking that button on a particular date will set that date as the `selectedDate` state in the `App` component.

To do this, we need to do the following:

- Write a method `handleForecastSelect` on the App component, which receives a date as a parameter, and sets that date as the selected date in the component state.
- Add a 'More details' button to the `ForecastSummary` component.
- Connect the function to the button, so that when we click the button, the function gets called with the date for that forecast.

## Setting state in a handler function

Lets start by adding the handler function. Add the following code to your `App` component, between the `constructor` and `render` functions:

```js
handleForecastSelect(date) {
  this.setState({
    selectedDate: date,
  });
}
```
This is pretty simple - the function gets passed a date, and we use the `this.setState` method to set that date on our state object.

`this.setState` is a method that gets added to the component by extending from `React.Component`.

So what does it do?
Firstly, it sets the given values on the `this.state` object. Something to note is that it **merges** the value into `this.state` rather than setting the whole `this.state` object.

Imagine having a state object with 10 values in it. It would be pretty cumbersome if every time we wanted to update the `selectedDate` property of our state, we had to re-set the other 9 values too.

Additionally, you might be wondering why we don't just do `this.state.selectedDate = date;` rather than using `this.setState`, which would also change the value of the selectedDate property on our state object.

The reason is that `setState` also tells React that this component and its children need to be re-rendered with the updated state - if you mutate a value in your state object manually, your component will not re-render with the updated values.

## Adding the More Details button with event handler

In the `ForecastSummary` component, under the rest of the markup, render a html `button` element, with the text "More details" (`<button>More details</button>`).

If you look at your app in the browser now, you should see the button. So what happens when we click it? Hopefully, the answer is nothing - because we haven't told it to do anything.

To make the button respond to being clicked, we need to add an **event handler** to it. An event handler is just a function that gets triggered by an **event**. There are lots of different types of events - window events, such as **load**, mouse events (**hover**, **click**, **scroll**), keyboard events (**keyup**, **keydown**, **keypress**), plus loads more. Pretty much whenever anything happens to the DOM, particularly via user interactions, then an event will be fired. We can use event handlers to tap into these events and respond to them.

### [DOM Events List](https://www.w3schools.com/tags/ref_eventattributes.asp)

We want to respond to the event that gets triggered when our button gets clicked. We can register event handlers to DOM elements by adding an `on{Event}` attribute to the element. So to respond to clicks on our button, we need to add an `onClick` attribute to it. The value of this should be a function. For now, let's just make an anonymous function that logs a message to the console:

```jsx
<button onClick={() => console.log('Hello!')}>More details</button>
```

Now, if you click on the button, you should see the message being logged in your browser console.

However, the function we want to invoke should not just `console.log` a welcoming message - we want it to invoke the handler function we wrote earlier in our `App` component, and we want it to invoke that function with the relevant date passed as an argument.

Can you think of a way to pass the `handleForecastSelect` method from the parent `App` component down to the child `ForecastSummary` component?

If you said **props**, then well done - you're getting the hang of this!

As we know, in JavaScript we can pass around functions just like we can pass around any other values, such as strings or numbers. This means we can also pass functions as props. We need to pass the `handleForecastSelect` method from `App` into `ForecastSummaries`, and then we need the `ForecastSummaries` component to pass the method into each individual `forecastSummary`.

### Task
- In `App`, pass the `this.handleForecastSelect` method into `ForecastSummaries` as a prop called `onForecastSelect`. Don't forget to add this prop to your `PropTypes` in `ForecastSummaries`.
- In `ForecastSummaries`, you now have access to a prop called `onForecastSelect`, which is a function with the ability to set state in the `App` component. Pass this prop down from `ForecastSmmaries` to each individual `ForecastSummary` as a prop called `onSelect`. Again, don't forget to update your prop types in `ForecastSummary`.

Now each rendered `ForecastSummary` has access to the `handleForecastSelect` method from `App` (although in the scope of `ForecastSummary`, it's referred to as `props.onSelect`). This means that `ForecastSummary` has the ability to set state in the `App` component.

We can invoke this method in the `onClick` function on our button.

```jsx
<button onClick={() => props.onSelect()}>More details</button>
```

Remember, we wanted to pass in the date to this function:

```jsx
<button onClick={() => props.onSelect(props.date)}>More details</button>
```

And there we have it - we now have the ability to select a date from our weather forecast to see the full forecast for that date... almost!

If you try and click the button now, you should see a message like `TypeError: Cannot read property 'setState' of undefined`.

Where are we trying to use the `setState` method? It's in `App` in the `handleForecastSelect` method. We have the line `this.setState(...`.

The error message therefore tells us that `this` is `undefined` when we try to invoke the function.

(We are trying to access the `setState` property of `this`, the error is that we can't access the property `setState` of undefined, therefore `this` is `undefined`).

Why would this be?

When we define the method, we would expect `this` to be the component itself - just like we would expect it to have been our `Pet` or our `Ship` objects with our object oriented projects from earlier in the course.

The problem is that in this case we are only passing the reference to the method itself, and not a reference to the whole component. Compare this to the ship and pet examples where we never treated the `dock` method or `walk` method in isolation, we always did `ship.dock()` or `pet.walk()`. Invoking methods in this way is how the method knows what the value of `this` is.

In our case, when we passed the method into a different component as props, we have lost sight of what `this` is.

This is because in JavaScript classes, methods are not **bound** to the instance by default. To solve the problem, we need to **bind** the method that we want to pass as props to the component it belongs to. Add the follwing to your `App` constructor method:

```js
this.handleForecastSelect = this.handleForecastSelect.bind(this);
```

The `bind()` method is a method on all functions creates a new function that, when called, has its `this` keyword set to the provided value.

By doing the above, we create a copy of `handleForecastSelect`, which always knows that `this` is supposed to be.

You will probably find yourself having to do this a lot in React when passing around event handler functions. It's a little bit confusing and certainly not very elegant, but it's worth knowing how to recognise and fix the problem.

If you click the button now, you should see your selected forecast being updated, as expected.

## [Next Step: Fetching external data - Lifecycle methods](step-15.md)

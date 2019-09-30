# Step 13 - Stateful components

As we know, state refers to the values stored in program at a given point in time.

So far, the state of our application never changes - we have a static json file with our data, and that data never changes. Our application doesn't do anything with the data, apart from pass it into components to get rendered.

Because of the lack of state in our application, all of the components we have created so far have been **stateless** components (you may see the terms stateless, functional and pure components, which can be used interchangeably).

A stateless component is just a JavaScript function, which receives a `props` parameter, and returns some JSX. Using stateless components is normally preferable where possible. They are the most simple type of component, and they actually have performance benefits too.

However, in most React apps that do anything interesting, we will want to use state. State management is one of the most important parts of learning React. State allows us to keep track of how the user has interacted with our app.

- If a user fills out a form field, we keep track of their input in state
- If a user selects an item from a list, we keep track of the selected item
- If a user logs in to the site, we can store their details in state

We can use this managed state to respond to user input accordingly

- We can validate the form values they have entered
- We can display the selected item
- If a user is not logged in, we can prevent a page or component from being displayed

Basically all interesting things you would ever want to do will involve state management.

As you've probably guessed, in this step we are going to create a stateful component - more specifically, we are going to turn our `App` component from a stateless one to stateful one.

## Classes and Class Components
Going back to the object-oriented principles we learned at the start of the course, we can encapsulate related state and behaviour in an object using the prototype/constructor pattern.

To create a stateful component, we can do the same - the only difference is that in React, it is preferred to use the ES6 class syntax.

### [ES6 Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
### [More ES6 Classes](https://scotch.io/tutorials/better-javascript-with-es6-pt-ii-a-deep-dive-into-classes)

Behind the scenes, Classes in JavaScript are the same as the Proto/Constructor pattern. The only difference is syntax.

Going back to our Virtual Pet, using Proto/Constructor we had this code to set the properties.

```js
function Pet(name) {
  this.name = name;
}
```

using classes, this would look like this:

```js
class Pet {
  constructor(name) {
    this.name = name;
  }
}
```

to add a method to our Pet, we would add it to the prototype:

```js
Pet.prototype.sayHello = function() {
  return `Hi, my name is ${this.name} and I'm a talking pet.`;
}
```
using class syntax, this function would go inside of the class body:

```js
class Pet {
  constructor(name) {
    this.name = name;
  }

  sayHello() {
    return `Hi, my name is ${this.name} and I'm a talking pet.`;
  }
}
```

To create a React component using classes, we would do something like this:

```jsx
class MyComponent extends React.Component {
  render() {
    return (
      <p>{this.props.message}</p>
    );
  }
}
```

### [Converting a functional component to a class](https://reactjs.org/docs/state-and-lifecycle.html#converting-a-function-to-a-class)

There are a few slight differences between a plain class like our `Pet`, and this React class component.

- `extends` - your class component should **inherit** from `React.Component` using the `extends` keyword - this gives the component some built in behavours that it needs to function correctly. Note also how the React component does not have a `constructor` method. This is because it inherits is constructor method from the parent, `React.Component`, so does not need one. If you want to, you can write your own constructor method, but the most basic class component does not need one.
- `render` method - every React class component should have at least a `render` method - this returns the JSX that you want to be rendered (the same as a pure/functional/stateless function would). You can add whatever other methods you want to the class, but `render` is the minimm requirement.
- `props` -> `this.props` - in a functional component, we always have access to the props, because all of the code is written inside of one function. When working with class components, the props get passed into the `constructor` method of `React.Component`, and can only be referenced directly there. In other methods, the props can be referenced as `this.props` instead.

## Challenge 1: Converting App into a class component

At the moment, your `App` component is a stateless component.

This first part of this walkthrough requires you to use the example and the guide from the React documentation (both above), to convert our `App` component into a basic class component.

Remember, your class needs to extend `React.Component`, and it should have a render method, which returns the JSX statement from the existing stateless component.


## State
As well as props, class components also have a `this.state` property. By default, this is `null`.

To set the initial state of a component, we need to add a `constructor` method to our component, which looks something like this:

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      message: 'Hello World',
    };
  }

  render() {
    return (
      <p>{this.props.message}</p>
    );
  }
}
```

Things to pay attention to here:
- The constructor method receives props as a parameter.
- When we write our own constructor method, we overwrite the constructor method of the parent class (`React.Component`) - in order to retain the behaviour defined in the parent, we should call `super` in our constructor. `React.Component` needs to be passed the props, so we do that too. As a rule, whenever you create a sub-class (in any context, not just React), you should call `super` if you define a new constructor.
- We set `this.state` to be an object. You should always set your state to be an object. The state object can contain ANY values you want. But `this.state` should always be an object.

We can then use our state in the render method:

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      message: 'Hello World',
    };
  }

  render() {
    return (
      <div>
        <p>{this.props.message}</p>
        <p>{this.state.message}</p>
      </div>
    );
  }
}
```

## Challenge 2: Storing the selected forecast in state

For the next part of this step, you will need to add some state to your component.

Complete the following tasks:

- add a `constructor` method to your `App` component
- set an initial value of `this.state` to be an object with a `selectedDate` property.
- Set the initial value of the `selectedDate` to the `date` value of your first `forecast` prop.
- In your render method, update the forecast you are passing to the `ForecastDetails` component so that it receives the forecast in your props that has a date matching the `selectedDate`.

In the next part of the walkthrough, we will be looking at updating the state of the `App` component based on user input.

## [Walkthrough](solutions/step-13.md)
## [Next Step: Modifying State & Event Handlers](step-14.md)

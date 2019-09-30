# Step 4 - Thinking in Components

For this weeks challenge, we are going to be making a 5 day weather forecasting app.

The data will be coming from a Web API, and will be in [this format](forecast.json). At first, we will just use this josn file for our data, and we will look about bringin in live data from the internet later on.

**N.B.** *The date property on each forecast object is in [unix time in milliseconds](https://en.wikipedia.org/wiki/Unix_time) - the number of milliseconds that have passed since 1st Jan 1970 00:00:00:0000. Timestamps in this format are a standard way of representing date information.*

As an MVP, we are going to implement the following features:

* Users should be able to see the name and country of the city the forecast is for.
* Users should be able to see a summary of each day of the forecast, including the date, general description of the weather that day, and maximum temperature.
* Users should be able to click on one of the summaries to view all of the forecasted information for that date

The app will look something like this:

![App](images/app.png "App")

Your challenge in this step doesn't involve any code - you're just going to plan out what you want your solution to look like.

Your challenge is to come up with the following details.

* Using the screenshot, what components do you think the UI can be broken down into?
* What props will each component need in order to render correctly? That is, what pieces of data will it need?

Discuss these questions with your pair, and make notes on your answers. Feel free to draw diagrams etc to help you out.

Once you're done, take a look at the walkthrough and compare what you have to our solution.

If you're happy you've understood how these components have been broken down, then move onto step 5 - it's time to start building the application!

## [Walkthrough](solutions/step-4.md)
## [Next Step: Rendering the location details](step-5.md)

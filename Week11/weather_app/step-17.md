# Step 17 - Error Handling

For the final step, we're going to keep the instructions minimal, so you have more of a challenge, and more room to experiment with your own solutions.

The issue we are having from the last step was that if we search for a city that doesn't exist, or just if there is an error fetching the data in general, we are not handling this.

To complete this task you will need to:

- Figure out how to handle an error response using axios.
- [Look at the API documentation](https://mcr-codes-weather.herokuapp.com/) - what are the possible status codes that you can get back? What do these codes mean? Which of these are errors?
- In your error handling code, set an appropriate error message in your app state based on the error code you receive.
- Conditionally render the error message from state - if there is a message, render it. If not then don't render anything.

Have you covered all of the bases? What happens if you perform an erroneous search, followed by a successful one?

When you're happy with the behaviour of your app, take some time applying some styles to it.

Take the time to go back over the walkthrough and other materials from this track. Are you happy with all of the topics covered? Can you think of any more functionality you might want to add? Are you satisfied with the tests you've written? 

Take the time to experiment by yourself, and focus on anything you're not totally comfortable with.

## :tada: Well done :tada:

You made it through probably the toughest track so far. Make sure your code is all committed and pushed to GitHub, take a breather and congratulate yourself on getting to this stage.

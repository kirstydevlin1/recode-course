# What is React?

React is - according to React - a JavaScript library for building user interfaces.

It is a very popular open-source library created and maintained by Facebook. It's popular because it is simple, powerful and performant.

## Where does React fit in?
If you think of a web application as having both a backend (a layer that interacts with a database), and a frontend (the layer that speaks to, and retrieves data from, the backend), then React falls very firmly on the frontend. It allows us to take data from a backend and present it to the user in a more meaningful and interactive way. 

### The old days
In the history of the internet, the view layer would have typically been a static HTML file that got sent to the browser.

Moving beyond that, you get to template engines, where the data from the database could be passed into a HTML template, and then sent to the browser - slightly more exciting.

In both of these, to make the page interactive, you would have to load in external javascript files, and plugins such as jQuery. Think about the complexity of manipulating the DOM in the cruise ships we made earlier in the course. Those were the days.

### Single Page Applications (SPA's)
You have probably heard people talking about front-end and back-end development. If you think that front-end development means primarily knowing how to write HTML and CSS, then think again. We now live in the era of single page applications.

A single page application is exactly what it sounds like - an entire application that runs inside of a web page. It means that you only ever have to download one (normally empty) HTML document from a server. The JavaScript then takes over, and handles everything, without ever having to reload the page. Even displaying different "pages" actually happen within the same HTML document. This means that the UI is a lot faster, and the only thing you have to request from your server is raw data (JSON, like we have been doing in the last few weeks).

This structure, however, also means that front-end development involves a lot more than just writing HTML pages. You're not just making seperate web pages, but a whole application.

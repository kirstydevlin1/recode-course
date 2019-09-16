# Installing Node.js and npm

## What is [Node.js](https://nodejs.org/en/)?

"Node.js is an open-source, cross-platform JavaScript run-time environment for executing JavaScript code server-side.Node.js is an open-source, cross-platform JavaScript run-time environment for executing JavaScript code server-side.". - [Wikipedia](https://en.wikipedia.org/wiki/Node.js)

Simply put, Node.js allows us to write JavaScript that runs on a computer. It does have other benefits, but we'll discuss those in more detail as the course goes on.

## What is [npm](https://www.npmjs.com/)?

npm is JavaScript's package manager. Other developers write open source code which gets bundled up into what's called a _module_, which they publish to npm's registry. We can bring these modules into our own applications to save us having to re-invent the wheel (all developers to this believe it or not).

## Installation

We'll install Node.js and npm using Node Version Manager (nvm) - a simple bash script (grouping of terminal commands) allowing us to install and manage multiple versions of Node.js.

1. Open the Terminal.
2. Run the following command to install nvm:

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
```

3. Then install the latest LTS (long term support) Node.js version (at time of writing this is 8.9.4, but you can double check [here](https://nodejs.org/en/)):

```bash
nvm install 8.9.4
```

**Note:** On Ubuntu, after running the install script, if you get `nvm: command not found`, simply close your current terminal, open a new terminal, and try verifying again.

**Note:** On OS X, if you get `nvm: command not found` after running the install script, one of the following might be the reason:-
 - your system may not have a `.bash_profile` file where the command is set up. Simply create one with `touch ~/.bash_profile` and run the install script again
 - you might need to restart your terminal instance. Try opening a new tab/window in your terminal and retry.

If the above doesn't fix the problem, open your `.bash_profile` (`open -a TextEdit ~/.bash_profile`) and add the following line of code and save:

`source ~/.bashrc`

Then try the install command again.

4. To check Node.js is installed, run:

```
node -v
```

The console should output your installed version (i.e. `8.9.4`)

5. To check npm is installed, run:

```
npm -v
```

The console should output your installed version (i.e. `5.6.0`)

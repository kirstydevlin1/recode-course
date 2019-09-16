# Node CLI

Node comes with a command-line tool `node` to help you run JavaScript programs from your terminal.

There are two main ways to use it - by giving it a file to run, or by using the **REPL**

## Running files

Imagine you have a file called `hello.js`.

In that file, you have some simple JavaScript code:

```js
console.log('Hello, world');
```

To execute this code on your computer, you can pass the file to the `node` executable:

```
$ node ./hello.js
```

This should result in the words "Hello, world" appearing in your terminal. Congratulations.

Using this, you can run entire applications and websites, whatever you want to build, from your terminal.

## REPL

REPL stands for **Read-Eval-Print-Loop**. Any self respecting programming language/framework/runtime ships with one, and Node is no different.

What does this mean though?

- READ - the program sits there, waiting for you to type something in. When you type something and press the return key, it reads what you've entered.
- EVAL - the program evaluates what you just typed
- PRINT - the program prints the result of that evaluation to stdout
- LOOP - the program goes back and waits for you to type something else

Basically, you can write code in and see the output straight away. This makes it really useful to use as a sandbox/playground type thing for quickly trying things out and experimenting.

To open the Node REPL, you can just use the `node` executable on it's own, and you should then see on a new line a `>` character followed by a slightly indented cursor. If so, that's it, you're in!

You can now just write JavaScript like you were writing it into a file:

```
> 'Hello';
'Hello'
> const hello = 'Hello';
undefined
> hello
'Hello'
> 1 + 2;
3
> true && false
false
> const add = (a, b) => {
... return a + b;
... }
undefined
> add(3, 5);
8
```

So if you ever need to try out an idea, or test how a function works for example, this is the place to do it.

N.B. In the above example, where we defined the `add` function:

```
 > const add = (a, b) => {
... return a + b;
... }
```

There are three dots at the start of the lines - this indicates that you have an unterminated block in your code (in this case, the function body, where we have the opening braces but no accompanying closing brace. Every time you open a new block, you'll get some more dots. The code won't evaluate until the block is closed.


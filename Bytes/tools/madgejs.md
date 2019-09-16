# MadgeJS
Madge is a tool for generating a visual graph of your module dependencies, so you can see which JavaScript module depends on which other.

[See repo here.](https://github.com/pahen/madge)

## Installation
To install madge you'll need to `npm` install it.

`npm -g install madge`

`-g` means it'll be installed globally, so it'll be available to be run against any JavaScript project you have!

To leverage the graphing capabilities, you'll also need to install a graphing library called `GraphViz`

Mac users can install this via `brew`

`brew install graphviz`

If you're using an Ubuntu machine, get it via `apt-get`

`apt-get install graphviz`

## Running It
Go to your project directory and run the command:

`madge --extensions js,jsx --image graph.svg src/`

- `extensions` flag tells madge which file extensions to scan the directory for. (in this case both jsx and js files)
- `--image` flag tells madge where to output the graph image
- last parameter `src` points to which directory you want to analyse, it's also possible to analyse a single file by passing its path.

After running madge, you should see an output like this:

```
Processed 10 files (1.5s)

✔ Image created at /Users/erselaker/mcrcodes/examples/weather-app/graph.svg
```

You can copy and paste the path to image to your Chrome address bar and :tada:

## Video Tutorial
I was experimenting myself when I recorded this video so excuse my mistakes.

[Video](https://drive.google.com/open?id=1zC4zL--ae1eYwszJ5U9KESu45gHnlsbI)


P.S: if madge is saying Processed 0 files, you're doing something wrong...
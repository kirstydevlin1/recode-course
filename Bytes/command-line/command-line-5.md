# Command Line - Advanced commands

## Streams

Every program on your computer has at least three [standard streams](https://en.wikipedia.org/wiki/Standard_streams) associated with it. Streams are channels used to connect the input and the output of the program to the environment (usually the terminal). 

An example of an input stream is keyboard. By reading from the input stream your program can read what you have typed on the keyboard. 
The screen is an example of an output stream. By sending data to the output stream, a program can print something on the screen.

You may be familiar with `console.log` in JavaScript - this function writes to the output stream.

There is also an error stream that is usually sent to the display as well but is used only to print error messages. It's not something you normally have to worry about, but it's good to know it exists.

For example, when you run the command `ls ~`, the list of files in your home directory gets written to the output stream.

The input stream is usually called **stdin**, the output stream is **stdout** and the error stream is called **stderr**.

## Pipes and redirection

Why do we need to know about streams?

Because we can redirect them and connect them to different programs, allowing us to perform some more sophisticated tasks.

**Pipes** allow you to redirect the output stream of one program to the input stream of another.

For example, when you use the command `ls -lA ~`, it will write a list of files to the terminal, but that list can potentially be quite long and take up a lot of screen space. We've also seen that the `less` command allows you to display some text on the screen temporarily.

By piping the list of files into the less command, we can display it temporarily, preventing it from being printed into the terminal.

`ls -lA ~ | less`

Give it a go.

In addition to piping stdout to another program, you can write it to a file using the redirect operator.

`ls -lA ~ > ~/Desktop/my-files.txt`

The above command will write the list of files to a file on your Desktop called `my-files.txt`

Give that a go too, and then `less` the file to see the result.

N.B. 
- If the file doesn't exist, `>` will create it.
- If the file exists, `>` will overwrite the contents of the file.
- You can use `>>` to append text to the end of a file rather than overwriting it.

## Using wildcards

So far when we have been listing files, we've been looking at only a handful at a time, and it's been easy to find what we want. But what if we were working on a big project with thousands of files?

Here's how you would list just the txt files in your Desktop directory:

`ls ~/Desktop/*.txt`

The asterisk acts as a **wildcard**, which matches any pattern.

What do you think the following commands do?

- `ls ~/new*.txt`
- `ls ~/*`
- `ls ~/*b*`

You can use wildcards with any command, not just `ls` - it's a built in feature of the terminal shell, not of any particular command.

### `find`

A more powerful version of `ls` is `find` - this will find all files in the specified directory, and also search recursively in sub-directories for matching files.

`find` takes one argument - the directory path to search within. 

You also need to pass in at least one flag, which specifies what to look for. You have quite a lot of options here, including things to do with the name of the file, the dates the files were created or updated, and whether the file is empty or not.

For a full list of options, check out the manual entry using `man find`

Say that you wanted to create a text file with all of the mp3 files (i.e. files where the name ends in `.mp3`) in your `~/Music` directory:

`find ~/Music -name "*.mp3" > my-mp3s.txt`

Assuming you have mp3 files in your Music directory, then you should now have a nice list of all of them.

### `grep`

We can also search for text inside of a file or stream using the grep command.

`grep` takes two arguments, the text to search for, and the file to search in.

It will print out each line that contains the matching text.

For example using the mp3 file you created above, `grep beatles my-mp3s.txt` would print out every line in the file that contained the text 'beatles'.

Using a pipe, you can see all of the .txt files in your home directory that have 'readme' in their name by doing the following:

`find ~ -name "*.txt" | grep readme`

If you want to use `grep` to search for text including spaces, you should wrap the text in "quote marks".

You can also make your search case-insensitive using the `-i` switch.

## Counting things  

You can get information on the length of a file using the `wc` (word count) command.

`wc my-mp3s.txt` should print out 3 numbers. These are respectively the line count, the word count and finally the character count of the file.

You can see each of these individually using `-l` `-w` and `-c`.

How many .txt files containing the text "readme" in the title you you have in your home directory?

`find ~ -name "*.txt" | grep readme | wc -l` will tell you!

## [Go to step 6](command-line-6.md)

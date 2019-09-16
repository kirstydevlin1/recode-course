# Command Line - Reading files

There are a number of commands you can use to quickly read the contents of a file without having to open the file in a text editor.

Having said that, create a file on your Desktop called `lorem.txt` and open it in your favourite plain-text editor. Type the following text into the file and save it:

```
Lorem ipsum dolor sit amet, consectetur adipiscing elit.
Fusce imperdiet maximus ipsum id iaculis.
Morbi ultrices quam et ullamcorper ullamcorper.
Vivamus dignissim nisl quis purus volutpat, eget rhoncus libero pulvinar.
Sed pretium dignissim ex, in sollicitudin ex suscipit nec.
Sed aliquet tempus nunc, ut vestibulum lacus placerat vel.
Sed auctor interdum diam non feugiat.
Suspendisse nec pellentesque mi, et elementum sem.
Aenean eu diam dui.
Vivamus a pretium diam, eget tempor tellus.
Cras gravida ligula orci, quis sodales dui fringilla eget.
Vestibulum varius consectetur volutpat.
Aliquam scelerisque non metus quis molestie.
Mauris quis convallis eros.
Proin maximus erat at urna consectetur pharetra.
Aenean tempus molestie arcu, id laoreet sem imperdiet id.
Etiam eu neque sed ante eleifend elementum.

Sed ac ex mi.
Cras ut mi nisi.
Nulla ac enim magna.
Nullam molestie ligula ultrices posuere aliquet.
Ut nec pulvinar nisl.
Suspendisse tempor arcu sed odio faucibus convallis.
Ut condimentum feugiat quam, a fringilla velit sodales vitae.
Morbi ultrices eros at lacus posuere, sit amet sollicitudin dolor sollicitudin.
Maecenas et urna sagittis, auctor est eget, sollicitudin nulla.
Phasellus commodo orci diam, et pulvinar sem pulvinar cursus.
Sed pretium enim ac urna feugiat, at ullamcorper est sodales.
Lorem ipsum dolor sit amet, consectetur adipiscing elit.
```

Now go back to your terminal.

## Viewing the contents of a file with `less`

You can now read the contents of this file using the `less` command.

`less lorem.txt`

This opens a preview of the file in your terminal. You can scroll up and down using your keyboard. When you're done, press q to quit and go back to your terminal.

## Printing the contents of a file with `cat`

You can print the contents of the file to the terminal more permenantly using the `cat` command.

`cat lorem.txt`

This command actually has more uses than just reading files - it is short for `concatenate`, and is used mainly for joining the contents of two files together. We'll come across it in that context shortly. 

## Printing the begining and ends of a file with `head` and  `tail`

To just view the first 10 lines of a file, you can use `head`. 

`head lorem.txt`

`tail` does the same with the end of the file.

`tail lorem.txt`

If you want to see more or less than the default 10 lines, you can pass the number in as a switch.

`tail -3 lorem.txt` will print the last 3 lines, for example.

`tail` also has a cool feature where it will keep watching a file for any new content to get added to the end.

If you are on a Mac run the following command:

`tail -f /private/var/log/system.log`

This is a log file of some of the processes that your computer is running. If you open or close an application (just open a new browser window, for example), you should see the output being updated.

This can be a useful tool when you are running a program and want to see what's happening internally.

To stop following the log file, just use `ctrl + c`

## [Go to step 5](command-line-5.md)

Let's get our project set up. Create a new repository in your projects directory like so:

```
$ mkdir virtual-pet
$ cd virtual-pet
$ git init
```

You now have a new git repository.

You can initialize an NPM project using the command `npm init`.  
This will lead you through some steps to create a package.json file, the config file for your project.

To install Jest, run `npm install -D jest`

This will install Jest as a development dependency.

Alter the package.json file so that the `test` value is `"jest"`.

This means that when you run `npm test`, it will run jest for you.

Now create a README file:

```
$ touch README.md
```

Add some basic explanation of the project to the README.md and then create a GitHub repo called 'virtual-pet'.

Get the SSH link for your repo, and link it to your local repository using `git remote add origin {the ssh link you just copied}` 

If you run `git status`, you will see that all of the files you've created are waiting to be tracked by git. However, you shouldn't commit your node_modules directory. To avoid this you can create a `.gitignore` file (note the dot at the start of the filename), and add the line `node_modules/` to it.

This file contains a list of files and directories that you want to keep out of git. Normally you would use it to keep node_modules, and any config files that might contains secret passwords out of git (and in particular off the internet on GitHub)

Once you've done that, check `git status` again to see that node_modules isn;t in the list of files.

If you're good, then add, commit and push the files up to GitHub and confirm that they are visible on GitHub.

Node that the contents of the README.md file are going to be extremely important. You are putting your code in public repositories on GitHub and the README.md file is the first thing that other programmers and potential employers are going to see when they look at your repo. It's okay to start with a placeholder at the moment, but you will want to keep updating your README as you go along, ensuring that it tells people about the project, how to get set up with it, how to contribute to it etc.

## [Step 2](../step2.md)
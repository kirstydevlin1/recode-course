# Deploying to GitHub Pages

GitHub offer a service called [GitHub Pages](https://pages.github.com/) that allows us deploy basic HTML/JavaScript projects online by pushing to a GitHub repository. You are allowed one website per GitHub account (don't create multiple accounts - there are other ways to host websites).

1. Go to [GitHub](https://github.com/) and click the **+** at the top and **New Repository**. 

2. **IMPORTANT**: To tell GitHub you want a repository to be deployed online, you have to name it *username*.github.io where username is your GitHub username.

3. Once you've given your repository its name, click **Create Repository**.

4. Now you'll want to add a new remote to your existing local repository (initialise a new local repo if you haven't already) that points to the new repository. Inside the command line, whilst in your project folder (which should have a git repo initialised inside of it) type the following:

```bash
git remote add deploy <https://github.com/username/username.github.io>
```

The URL above should match your newly created GitHub repository.

5. Now `git push` to your new remote:

```bash
git push deploy master
```

In anything up to 30 minutes time (it sometimes takes a while for your changes to propogate through GitHub's servers - you may be able to see it straight away) you should be able to see your project online by visiting *username*.github.io in your browser. 

Every time you make a change locally now, view the file inside your web browser and check *very carefully* (let's at least pretend we have many thousands of users relying on us to ensure our application works) that you're happy it works as it should. If it does then add and commit changes, and push up to your `deploy` remote.
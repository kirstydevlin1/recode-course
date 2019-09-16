# Installing Git

## What is Git?

Git is a free and open source distributed (it tracks individual directories and their subdirectories - otherwise known as a _repository_) version control system (allows us to create a timeline of our code) designed to handle everything from small to very large projects with speed and efficiency.

## Installation

### Linux

Open a Terminal and enter:

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
```

### Mac

You should have Homebrew installed by now. Open a Terminal and enter the following:

```bash
brew install git
```

### Configuring Git

You need to configure Git so that your name and email address appear on commits. You can do so with the following (replace details with your own):

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

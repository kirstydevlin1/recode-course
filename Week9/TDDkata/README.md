# TDD Kata

This week we're looking at writing our own JavaScript tests, before proceeding to write the code that makes them pass.

## Learning objectives

To be able to answer "yes" to the following questions:

- Can you write a test that describes the expected behaviour of a unit?
- Can you use that test as a reference to write some code for the unit?
- When you've passed the test, can you find ways to refactor the code?

## Concepts

- Test-Driven Development
- Unit Testing
- Jest
- Refactoring
- DRY - Don't Repeat Yourself

## Challenge

This week's challenge uses the [DIY Kata](https://github.com/recode-course/Week9/DIYKATA) repository on GitHub. You will be pairing so please choose driver/navigator roles between you now (it doesn't matter who goes first, as you will swap over, but if you were the driver first last week - and your partner wasn't - then you might want to consider navigating first this week). 

**Driver:**

* [ ] Fork the [repository](https://github.com/MCRcodes/diy-kata) to your own GitHub profile.
* [ ] Clone down your fork.
* [ ] Change directory into your cloned folder and run `npm install`.

**Navigator:**

You won't fork the existing repository, as you want to build on top of the work the current driver has done when you swap roles. The way around this is to clone down your partner's repository and push it up to an empty repository on your GitHub.

* [ ] Create a new repository on GitHub without a README called `diy-kata`.
* [ ] Clone down your partner's repository (always use the SSH URL) and change directory into it.
* [ ] Rename the `origin` remote of the local repository to your partner's username (`git remote rename origin <your partner's username>`)
* [ ] Create a new remote named `origin` and set it to the SSH URL of your newly created remote repository (`git remote add origin <your repository url>`).

**Driver:**

* [ ] Add a remote to your local repository pointing towards your partner's (`git remote add <your_partners_username> <your_partners_ssh_repository_url>`).
* [ ] Run `npm install`.

You can find out more about how this all works in our [:zap: Git Pong](../bytes/git/git-pong.md) byte.

**Both Pairs:**

* [ ] Start working through the challenges - step 1 is linked below.

## Challenges

1. [FizzBuzz](./step1.md)
2. [Boolean to word](./step2.md)
3. [Convert a Number to a reversed Array of digits](./step3.md)
4. [Human Years, Cat Years, Dog Years](./step4.md)
5. [How long will it take the train to reach its destination?](./step5.md)
6. [Bart, Lisa & Maggie](./step6.md)
7. [Find employer role in the company](./step7.md)

## [Go to step 1](./step1.md)

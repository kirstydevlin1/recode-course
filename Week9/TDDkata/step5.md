# How long will it take the train to reach its destination?

## Expected Behaviour

You're on a train to your friend's, and you need to send your friend a text to let them know when you'll be arriving.

Assuming you know the train's distance from your destination in miles, and you know how fast the train is going in miles per hour, you'll use a `reachDestination` function to output a string:

```
I should be there in 4.5 hours.
```  

The time should be rounded up to the nearest 0.5 hours (half an hour).

`reachDestination` has two parameters: `distance` and `speed` - it is expected that only arguments of a Number type will be passed. 

E.g.

```js
reachDestination(44, 10);
```

Would output:

```
I should be there in 4.5 hours.
```

Because `44 / 10` is `4.4`, which we round up to the nearest 0.5 to equal `4.5`.

## Assertion

- returns string with estimated time of arrival

## Run tests

```bash
npm run test -- reachDestination
```

---
**Don't see this on your diy-kata repo?**

Your repo probably isn't up to date with the remote. You can bring it up to date by adding the original repo back as a remote, and pulling from it with a rebase (a rebase takes new commits from the remote and slots them around yours):

```bash
git remote add mcrcodes git@github.com:MCRcodes/diy-kata.git
git pull --rebase mcrcodes master
```
---

## [Next Step: Bart, Lisa & Maggie](6_JoinNames.md)

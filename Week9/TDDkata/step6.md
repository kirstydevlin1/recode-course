# Bart, Lisa & Maggie

## Expected Behaviour

Your function should take an array of objects and concatenate the names together into a string, seperated by commas and an ampersand for the last name.

E.g.

Given an array of objects like so:

```js
[{
  name: 'Bart'
}, {
  name: 'Lisa'
}, {
  name: 'Maggie'
}]
```

Your function should return:

`'Bart, Lisa & Maggie'`.

It shouldn't be limited to just 3 names, so ensure you have assertions for any array length.

## Assertion

- returns string of names, seperated by commas and an ampersand

## Run tests

```bash
npm run test -- joinNames
```

---
**Don't see this on your diy-kata repo?**

Your repo probably isn't up to date with the remote. You can bring it up to date by adding the original repo back as a remote, and pulling from it with a rebase (a rebase takes new commits from the remote and slots them around yours):

```bash
git remote add mcrcodes git@github.com:MCRcodes/diy-kata.git
git pull --rebase mcrcodes master
```
---

## [Next Step: Find employer role in the company](7_EmployerRole.md)

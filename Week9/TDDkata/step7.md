# Find employer role in the company

## Expected Behaviour

Your function should have two parameters: `employeeName` (string) and `employees` (array).

Given an array of `employees`, and an `employeeName`, you should find and return that person's `role` in the company.

E.g.

If we have the following employees:

```js
const employees = [{
  name: 'Satti',
  role: 'Developer'
}, {
  name: 'Jenny',
  role: 'Sales Associate'
}, {
  name: 'Javid',
  role: 'Human Recommended Reading Assistant'
}]
```

When calling the `getEmployerRole` function like so:

```js
getEmployerRole('Javid', employees);
```

We would expect a return value of:

```js
'Human Recommended Reading Assistant'
```

## Assertion

- returns the employee's role in the company

## Run tests

```bash
npm run test -- getEmployerRole
```

## COMPLETED AMIGOS! 

# Human Years, Cat Years, Dog Years

## Expected Behaviour

When `humanCatDogYears` is passed a number (representing human years), it should return an array of three numbers. The first number should be the human years passed as an argument, the second element should be the equivalent cat years, and the third element should be the equivalent dog years.

E.g `humanCatDogYears(10)` should return `[10, 56, 64]` based on the formulas below.

### Formulas for calculating cat and dog years

#### Cat Years

15 cat years for first human year
+9 cat years for second human year
+4 cat years for each human year after that

#### Dog Years

15 dog years for first year
+9 dog years for second year
+5 dog years for each year after that

## Assertion

- returns array of human, cat and dog years when passed human years

## Run tests

```bash
npm run test -- humanCatDogYears
```

## [Next Challenge: How long will it take the train to reach its destination?](5_ReachDestination.md)

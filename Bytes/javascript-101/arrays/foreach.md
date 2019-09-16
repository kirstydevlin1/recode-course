# Array Iterators - `forEach`

The `.forEach` method iterates over every element in an array and every time it lands on an element it will call the callback function you provide, passing 3 arguments to your callback function's parameters (in order):

* `currentValue` - the value of the current element
* `index` - the index of the current element in the given array
* `array` - the array being iterated over (if you've assigned your array to a variable then you usually won't need this parameter)

## When to use `forEach`

`forEach` is great for when you want to iterate over an array and access one element at a time without modifying it's value.

## Example Scenario

Imagine a website such as _MailChimp_, where a business can create a mailing list that customers can sign up to. That business might create a new newsletter, which they want to send out to all of their customers. A `forEach` in this scenario might be used to iterate over the mailing list and to call a `sendEmail` function for each email.

### Code

```js
const sendEmail = (emailAddress) => {
  // you don't need to worry about what sendEmail might look like
}

const emails = [
  'mthurn@live.com', 
  'rgarcia@optonline.net', 
  'webdragon@comcast.net',
  'crandall@sbcglobal.net',
  'fangorn@hotmail.com'
]

emails.forEach((email, index) => {
  console.log('Sending newsletter to ' + email + ' - index ' + index + ' in the list of emails')
  sendEmail(email)
})
```

## [forEach on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

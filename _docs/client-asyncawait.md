---
title: Async / Await
permalink: /docs/client/asyncawait/
---

The Hudson-Taylor client has native support for promises, giving you another way to interact with it.

Calling `Client#call` without a callback, will return a promise you can use.

## Example with native promises

```js
var promise = client.call('math', 'add', {
  firstNumber: 123,
  secondNumber: 5432
})

promise.then(function (result) {
  console.log(result) // -> 5555
}).catch(function (err) {
  console.error(err)
})
```

## Example with JS Await keyword

You must have [Babel](http://babeljs.io/) (or something similar) set up before you can use the `await` keyword.
{: .notice--warning}

```js
try {
  let result = await client.call('math', 'add', {
    firstNumber: 123,
    secondNumber: 5432
  })
  console.log(result) // -> 5555
} catch (err) {
  console.error(err)
}
```

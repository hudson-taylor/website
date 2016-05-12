---
title: Async / Await
permalink: /docs/service/asyncawait/
---

The Hudson-Taylor service has native support for promises, giving you another way to interact with it.

If you pass a function to `Service#on` that returns a promise, that promise will be evaluated each time the method is called.

## Example with native promises

```js
s.on('add', function (data) {
  return new Promise(function (resolve, reject) {
    resolve(data.firstNumber + data.secondNumber)
  })
})
```

## Example with JS Await keyword

You must have [Babel](http://babeljs.io/) (or something similar) set up before you can use the `await` keyword.
{: .notice--warning}

```js
s.on('add', async function (data) {
  return data.firstNumber + data.secondNumber
})
```

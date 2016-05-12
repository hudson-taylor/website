---
title: Client Overview
permalink: /docs/client/overview/
---

## What is a Client?
 
The ht client is used to make calls against one or more ht services via their transport. You would use
a client from any code you wish to communicate to an ht service from, including other services. 

## Creating one

```js
var client = new Client({
  someService: new ht.Transports.TCP({ port: 1337 }),
  anotherService: new ht.transports.TCP({ port: 1338 })
})
```

## Invocation

```js
client.connect(function(err) {
  if(err) return console.error("There was an error connecting:", err)
  client.call("someService", "example", {
    some: "data"
  }, function(err, response) {
   console.log(err)      // -> undefined
   console.log(response) // -> "test data"
 })
})
```

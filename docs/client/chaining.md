---
layout: docs
title: Chaining
description: 
permalink: /docs/client/chaining/
---

# Chaining Calls

HT allows you to *chain* service calls, essentially allowing you to directly pass the result of one function call to another one.

To start a chaining call, just call *Client#chain()* as many times as you wish, passing in the relevant service/method/data you wish.

Once you have your 'chained' calls setup, execute them by calling *Client#end()*.

## Example

```js

client.chain('service', 'echo', 'olleh')
      .chain('service', 'reverse') // will use the result from the previous call as data input
      .chain('service2', 'addstring', ' world') // explicitly set data for this call
      .end(function(err, result) {

        console.log(result); // -> "hello world"

      });

```

## Sequential Calls

When you chain calls back-to-back to the same service, HT automatically optimises this and turns them into **a single call**.

<img src="/images/sequential.png" style="width: 100%;">
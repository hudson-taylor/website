---
layout: docs
title: Overview
description: 
permalink: /docs/client/overview/
---

## What is a Client?
 
The ht client is used to make calls against one or more ht services via their transport. You would use
a client from any code you wish to communicate to an ht service from, including other services. 

## Creating one

```js
var client = new Client();

// or

var transport = new ht.Transports.TCP({ port: 1337 });
var client = new Client({
  someService: transport
});
```

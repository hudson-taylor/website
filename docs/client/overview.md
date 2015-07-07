---
layout: docs
title: Overview
description: 
permalink: /docs/client/overview/
---

## What is a Client?

TODO

## Creating one

```js
var client = new Client();

// or

var transport = new ht.Transports.TCP({ port: 1337 });
var client = new Client({
  someService: transport
});
```

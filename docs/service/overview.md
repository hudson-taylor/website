---
layout: docs
title: Overview
description: 
permalink: /docs/service/overview/
---

## What is a Service?

TODO

## Creating one

Before you create a service, you need to understand how **Transports** fit in. Head over **LINK** here and read the overview.
For these examples, we are going to use the TCP transport.

```js
// create a TCP transport that communicates over port 11111
var transport = new ht.Transport.TCP({ port: 11111 });

// Initialise a new Service instance
var service = new ht.Service(transport);
```

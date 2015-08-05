---
layout: docs
title: Overview
description: 
permalink: /docs/service/overview/
---

## What is a Service?

A Hudson Taylor service is a container for all of your callable methods. It is one side of the puzzle piece, the other being a *Client*.

A single service can have many methods, and many transports - if you were to pass both a TCP and HTTP transport, you would be able to access it over both, depending on your situation (mobile vs. browser etc).

## Creating one

Before you create a service, you need to understand how **Transports** fit in. Head over **LINK** here and read the overview.
For these examples, we are going to use the TCP transport.

```js
// create a TCP transport that communicates over port 11111
var transport = new ht.Transport.TCP({ port: 11111 });

// Initialise a new Service instance
var service = new ht.Service(transport);
```

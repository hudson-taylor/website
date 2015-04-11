---
layout: docs
title: Local Transport
description: 
permalink: /docs/transports/local/
---

The Local transport is special. Instead of binding to a socket like the TCP transport, or communicating over HTTP, like the HTTP Transport, it mounts a service as a internal function.

<blockquote class="ht-callout ht-callout-info">
  <p>
    Using the local transport is fantastic for development, but you may want to look into using another transport if you're planning to support horizontal scaling.
  </p>
</blockquote>

## Example

```js

var transport = new ht.Transports.Local();

// Make sure you pass the same instance to
// both your service, and your client.

var service = new ht.Service(transport);
var client = new ht.Client({
  name: transport
});

```
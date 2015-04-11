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

## Options

| Name  | Type   | Required | Example     | Default   | Description                   |
|-------|--------|----------|-------------|-----------|-------------------------------|
| host  | string |          | "127.0.0.1" | "0.0.0.0" | Network address to listen on. |
| port  | number | ✓        | 1234        | N/A       | Network port to listen on.    |
| path  | string |          | "/endpoint" | "/ht"     | Path to accept requests on.   |

## Example

```js

var config = {
  host: "127.0.0.1",
  port: 1337,
  path: "/endpoint"
};

var transport = new ht.Transport.HTTP(config);

```
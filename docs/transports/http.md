---
layout: docs
title: HTTP Transport
description: 
permalink: /docs/transports/http/
---

The HTTP transport uses http requests to communicate.

<blockquote class="ht-callout ht-callout-warning">
  <p>
    Only use this transport if you cannot use the TCP Transport. It has a <b>much</b> larger overhead, and if therefor less efficient.
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
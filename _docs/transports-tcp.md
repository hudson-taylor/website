---
title: TCP Transport
permalink: /docs/transports/tcp/
---

The TCP Transport uses long-lived sockets for efficient communication with the remote service.

## Installation

The TCP transport is not bundled with Hudson Taylor by default.

To install:

```
npm install ht-tcp-transport --save
```

## Options

| Name  | Type   | Required | Example     | Default   | Description                   |
|-------|--------|----------|-------------|-----------|-------------------------------|
| host  | string |          | "127.0.0.1" | "0.0.0.0" | Network address to listen on. |
| port  | number | ✓        | 1234        | N/A       | Network port to listen on.    |

## Example

```js
var htTCPTransport = require('ht-tcp-transport')

var transport = new htTCPTransport({
  host: "127.0.0.1",
  port: 1337
})
```

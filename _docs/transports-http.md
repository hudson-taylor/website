---
title: HTTP Transport
permalink: /docs/transports/http/
---

The HTTP transport uses http requests to communicate.

## Installation

The HTTP transport is not bundled with Hudson Taylor by default.

To install:

```
npm install ht-http-transport --save
```

## Options

| Name    | Type       | Required | Example       | Default   | Description                            |
|---------|------------|----------|---------------|-----------|----------------------------------------|
| host    | string     |          | "127.0.0.1"   | "0.0.0.0" | Network address to listen on.          |
| port    | number     | ✓        | 1234          | N/A       | Network port to listen on.             |
| path    | string     |          | "/endpoint"   | "/ht"     | Path to accept requests on.            |
| ssl     | Object     |          | { cert, key } | N/A       | Enable SSL                             |
| agent   | http.Agent |          |               | N/A       | To manage connection persistence       |
| timeout | number     |          | 1800          | N/A       | Timeout before the socket is connected |
## Example

```js
var htHTTPTransport = require('ht-http-transport')
var http = require('http')

var keepAliveAgent = new http.Agent({ keepAlive: true })
var transport = new ht.Transport.HTTP({
  host: "127.0.0.1",
  port: 1337,
  path: "/endpoint",
  ssl: {
    cert: "...",
    key: "..."
  },
  agent: keepAliveAgent,
  timeout: 1000
})
```

---
layout: docs
title: TCP Transport
description: 
permalink: /docs/transports/tcp/
---

The TCP Transport uses long-lived sockets for efficient communication with the remote service.

## Options

| Name  | Type   | Required | Example     | Default   | Description                   |
|-------|--------|----------|-------------|-----------|-------------------------------|
| host  | string |          | "127.0.0.1" | "0.0.0.0" | Network address to listen on. |
| port  | number | ✓        | 1234        | N/A       | Network port to listen on.    |

## Example

```js

var config = {
  host: "127.0.0.1",
  port: 1337
};

var transport = new ht.Transport.TCP(config);

```
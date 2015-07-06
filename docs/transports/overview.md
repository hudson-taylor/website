---
layout: docs
title: Transport Overview
description: 
permalink: /docs/transports/overview/
---

# Transports

Hudson Taylor supports a multitude of ways to communicate between *Client* and *Service*, these are known as *Transports*.

Transports send and receive a JSON payload however they want, this makes transports very versatile.

## Bundled

There are 3 transports that come bundled with HT, these are

| Name  | Description |
|-------|-------------|
| TCP   | Uses long lived sockets to communicate. This is great for high performance workloads.             |
| HTTP  | Uses HTTP requests to communicate. Not very performant. Required if only HTTP traffic is allowed. |
| Local | Mounts services locally. Good for development. Cannot mount remote services.                      |

## Non-bundled

| Name                                                      | Supported | Description                             |
|-----------------------------------------------------------|-----------|-----------------------------------------|
| [SQS](https://github.com/hudson-taylor/ht-sqs-transport)  | ✓         | Uses Amazons SQS service to communicate |

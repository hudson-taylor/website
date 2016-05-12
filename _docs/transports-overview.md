---
title: HT Transports
permalink: /docs/transports/overview/
---

Hudson Taylor supports a multitude of ways to communicate between *Client* and *Service*, these are known as *Transports*.

Transports send and receive a JSON payload however they want, this makes transports very versatile.

## Officially Supported

There are 3 officially supported transports.

* [HTTP](/docs/transports/http/) - Uses HTTP requests to communicate across services
* [TCP](/docs/transports/tcp/) - Uses long lived TCP sockets to communicate
* [Local](/docs/transports/local/) - Useful for development and very small deployments, communicates in-process.

## Unofficially Supported

* [PeerJS](https://github.com/hudson-taylor/peerjs-transport) - Browser-based WebRTC transport
* [SQS](https://github.com/hudson-taylor/ht-sqs-transport) - Uses Amazons SQS service to communicate between processes 

---
title: "What is Hudson Taylor?"
permalink: /docs/what/
---

Hudson Taylor provides a set of building blocks that you can use to develop _documented_, _schema validated_, _error recoverable_ services.

## Concepts

### Schemas

HT comes with a schema validation library you can use.

We suggest that you add schemas to all of the endpoints you create (even if those schemas are loose)

If you use the built in schema library, you can also automatically generate documentation for all of your endpoints

### Transports

HT builds on a concept that we call 'transports', basically just a way of transferring data from one place or another.

You may chose to use something as simple as JSON over HTTP, or something more complicated like protobufs over a P2P WebRTC connection

### Get started

See the [Quick Start guide](/docs/quick-start-guide/) to get started!

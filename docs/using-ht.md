---
layout: docs
title: Using HT
description: Basic overview of HT and its surrounding components.
permalink: /docs/using-ht/
---

## What is HT?

Hudson Taylor is a set of libraries for building automatically documented, well validated, service-oriented platforms.

There are a few core pieces that you should know about:

- **Service** - A service listens to incoming requests
- **Schema** - Each incoming request *should* have a schema associated with it
- **Client** - A client is used to initiate requests to a service.
- **Transport** - A transport is how a client and service talk to each other

All service APIs have a schema that both document expectations as well as validates and pre-processes incoming data, this allows you to be sure of what data you're recieving, but also lets you automatically generate documentation based on the data you're expecting!

## Installation

Here is how to install HT on each platform we support.

<blockquote class="ht-callout ht-callout-info">
  <p>
    At the moment HT only has a Node.JS library, we're hoping to change that very soon!
  </p>
</blockquote>

### Node.js

**Install**

```sh
$ npm install hudson-taylor ht-schema --save
```

## Quick Start

TODO, copy from readme?
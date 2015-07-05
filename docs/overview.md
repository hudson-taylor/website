---
layout: docs
title: Using HT
description: Basic overview of HT and its surrounding components.
permalink: /docs/overview/
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

To get started, there are 3 things you need to do:

1. Decide on a method of communication to use, HTTP, TCP or something else.
2. Create a service and add methods to it.
3. Create a client to connect to that service.

### Preamble

Require things we need to...

```js
var ht = require('hudson-taylor');
```

### 1. Decide on a transport

HT comes bundled with 3 different transport types, **HTTP**, **TCP** and **Local**, to get more info go to their respective documentation pages.

```js
// Pick one of the following and change the options if you wish
var transport = new ht.Transports.HTTP({ host: "127.0.0.1", port: 8080 });
var transport = new ht.Transports.TCP({ host: "127.0.0.1", port: 8080 });
var transport = new ht.Transports.Local();
```

### 2. Create a service

To create a service you need to give it a transport to use.

```js
var service = new ht.Service(transport);
```

Next, we need to add a method which can be called! To do this, we use the *.on* function on the service.

```js
// This function will just echo the data back to the client
service.on("echo", function(data, callback) {
  return callback(null, data);
});
```

Lastly, if you chose the **HTTP** or **TCP** transport, we need to make the service start listening for connections..

```js
service.listen(function(err) {
  if(err) {
    console.error("There was an error listening:", err);
  }
});
```

### 3. Create a client

Now that we have a service, we need a client to connect to it!

```js
var client = new ht.Client({
  // When using the client, or service above is now called "test"
  test: transport
});
```
<blockquote class="ht-callout ht-callout-info">
  <p>
    You can add multiple services to a single client, just pass multiple object keys when initialising.
  </p>
</blockquote>

Like a service, if your client uses a **HTTP** or **TCP** transport, you need to connect.

```js
client.connect(function(err) {
  if(err) {
    console.error("There was an error connecting:", err);
  }
});
```

Now all of our setup is done, we can call our echo method!

```js
client.call("test", "echo", "test data", function(err, response) {
  console.log(err);      // -> undefined
  console.log(response); // -> "test data"
});
```
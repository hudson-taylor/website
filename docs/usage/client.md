---
layout: docs
title: Creating a Client
description: 
permalink: /docs/usage/client/
---

## What is a Client?

TODO

## Creating One

### new Client([services])

Passing an optional object as an argument will mount those services on the client. You can also do this after the fact, see *Client.add*.

#### Example

```js
var client = new Client();

// or

var transport = new ht.Transports.TCP({ port: 1337 });
var client = new Client({
  someService: transport
});
```

## Instance Methods

### Client.add(name, transport)

*Client.add* is used to add another service to this client. It takes the name of the service, and an instance of a transport.

#### Example

```js
var transport = new ht.Transports.TCP({ host: "10.1.1.3", port: 1337 });
client.add("otherService", transport);
```

### Client.connect(callback)

*Client.connect* initiates a connection to the remote service, if any of the transports you're using require it.

*callback* will be called when services are connected, with an optional error.

### Client.disconnect(callback)

*Client.disconnect* disconnects all transports.

*callback* will be called when services are disconnected, with an optional error.

### Client.call(service, method[, data][, callback])

*Client.call* will call *method* on the remote service *service*, passing optional *data*, and then calling *callback* with an optional error, and the response from call.

#### Example

```js

client.call("users", "list", function(err, users) {
  
});
```

### Client.before(fn, options)

*Client.before* adds a function that will get executed **before** the data is sent to the remote service.

The optional options object can have the following properties.

| Name    | Type   | Example         | Description                                              |
|---------|--------|-----------------|----------------------------------------------------------|
| method  | string | "service1"      | Restrict this middleware to only the call for *service*. |
| service | string | "reverseString" | Restrict this middleware to only the call for *method*.  |

### Client.after(fn, options)

*Client.after* adds a function that will get executed **before** the data is returned to the client, but **after** the remote service has given a response.

The optional options object can have the following properties.

| Name    | Type   | Example         | Description                                              |
|---------|--------|-----------------|----------------------------------------------------------|
| method  | string | "service2"      | Restrict this middleware to only the call for *service*. |
| service | string | "reverseString" | Restrict this middleware to only the call for *method*.  |

### Client.prepare(service, method, data)

*Client.prepare* is similar to *Client.call*, but will return a function that you can call later, instead of immediately.

#### Example

```js

var findUsers = client.prepare("users", "list");

findUsers(function(err, response) {
  // etc
});
```

### Client.chain(service, method, data)

**TODO**: document this, explain how data is transfered to next call in chain, and how sequential calls work

### Client.end(callback)

**see above**

#### Example

```js

chainedCall.end(function(err, response) {
  
});
```

###Client.remote(service, method, data, callback)

<blockquote class="ht-callout ht-callout-warning">
  <p>
    <i>Client.remote</i> has been deprecated in favour of <i>Client.call</i>
  </p>
</blockquote>

###Client.addSchema(service, method, schema)

This allows you to add a schema that validates your data after it's returned.

```js

client.addSchema("service", "method", s.Object({
  hello: s.String()
}));

client.call("service", "method", function(err, response) {

  // you can be sure that 'response.hello' is a string
  // if it's not - an err will be set to a validation error.

});

```

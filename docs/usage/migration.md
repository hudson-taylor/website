---
layout: docs
title: Migrating from HT1.x
description: How to migrate from HT1 to HT2
permalink: /docs/usage/migration/
---

The current version of Hudson-Taylor is a complete rewrite of HT1, it features numerous upgrades, fixes and features - therefore the old Hudson-Taylor has been **deprecated**.

One of the main changes for HT2 is the separation of 'Transports' from the Service/Client code. This allows you to 'plug' different methods of communication in, and allows you to use multiple at the same time.

The following snippets will be examples on how to upgrade your HT1.x code to HT2.x

---

## Client

The code for instantiating a client has not changed much, only that you pass a new _transport_ as the second argument for adding a service.

Note, the _remote_ function has been deprecated in favour of _call_ (they both have the same function signature)

### HT1.x

```js

var s = new ht.Services();

s.connect("myServices", new ht.HTTPClient("myService", "localhost", 7001));

s.remote("myServices", "echo", {
  input: "Hello World!"
}, function(err, response) {
  // response -> "Hello World!"
});

```

### HT2.x

```js

var s = new ht.Client();

s.add("myServices", new ht.Transports.HTTP({
  host: "localhost",
  port: 7001
});

s.call("myServices", "echo", {
  input: "Hello World!"
}, function(err, response) {
  // response -> "Hello World!"
});

```

## Service

Likewise, creating a service is pretty identical, the only difference is you have to pass the transport you wish to use as an argument when you instantiate a service. 

### HT1.x

```js

var server = new ht.Server();
server.add("myService", function(s, ready) {
  s.on("echo", s.Object({
    input: s.String()
  }), function(data, callback) {
    callback(null, data.input); // echo data back
  });
});

server.listenHTTP({ port: 7001 });

```

### HT2.x

```js

var service = new ht.Service(new ht.Transport.HTTP({
  host: "localhost",
  port: 70001
}));

service.on("echo", {
  input: s.String()
}, function(data, callback) {
  callback(null, data.input); // echo data back
});

service.listen(function(err) {
  // check for error, obviously
});

```

## Local Service

For a local service, you need to instantiate a **Local** transport, and then pass the **same** instance to both the service, and client you create. 

### HT1.x

```js

var s = new ht.Services();

s.connect("myService", new ht.LocalService("myService", function(s, done) {
  s.on("echo", s.Object({
    input: s.String()
  }), function(data, callback) {
    callback(null, data.input);
  });
});

s.remote("myService", "echo", {
  input: "hello"
}, function(err, response) {
  // response -> "hello"
});

```

### HT2.x

```js

var transport = new ht.Transport.Local();

var service = new ht.Service(transport);

service.on("echo", {
  input: s.String()
}, function(data, callback) {
  callback(null, data.input);
});

var client = new ht.Client();

client.add("myService", transport);

client.call("myService", "echo", "hello", function(err, response) {
  // response -> "hello"
});

```
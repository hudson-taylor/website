---
title: "Quick-Start Guide"
permalink: /docs/quick-start-guide/
---

## Installation

```sh
$ npm install hudson-taylor --save
```

At the moment HT only has a Node.JS library, we're hoping to change that very soon!
{: .notice--info}

## Let's go

To get started, there are 7 things you need to do:

1. Decide on a method of communication to use, HTTP, TCP or something else.
2. Create a service
3. Add methods to our service
4. Start our service
5. Create a client
6. Connect our client
7. Use our client!

### Preamble

Require things we need to...

```js
var ht = require('hudson-taylor')
```

### 1. Decide on a transport

HT officially supports 3 different types of transports - `HTTP`, `TCP` and `Local` (to get more info go to their respective documentation pages)

The `Local` transport comes bundled with the core HT library, but `HTTP` and `TCP` are shipped separately.
{: .notice--info}

#### Local

```js
var transport = new ht.Transports.Local()
```

#### HTTP

```js
var httpTransport = require('ht-http-transport')

var transport = new httpTransport({
  host: '127.0.0.1',
  port: 8080
})
```

#### TCP

```js
var tcpTransport = require('ht-tcp-transport')

var transport = new tcpTransport({
  host: '127.0.0.1',
  port: 8080
})
```

### 2. Create a service

To create a service you need to give it a transport to use.

```js
var service = new ht.Service(transport)
```

### 3. Add a method

Next, we need to add a method which can be called. To do this, we use the `.on` function on the service.

```js
// This function will just echo the data back to the client
service.on('echo', function (data, callback) {
  return callback(null, data)
})
```

### 4. Start the service

Lastly, if you chose the `HTTP` or `TCP` transport, we need to make the service start listening for connections..

```js
service.listen(function (err) {
  if (err) {
    console.error('There was an error listening:', err)
  }
})
```

### 5. Create a client

Now that we have a service, we need a client to connect to it.

You can add multiple services to a single client, just pass multiple object keys when initialising.

You can also add services to a client at runtime by calling `Client#add`
{: .notice--info}

```js
var client = new ht.Client({
  // When using the client, or service above is now called 'test'
  test: transport
})
```

### 6. Connect the client

If you use a transport that requires a permanent connection (like our `TCP` transport), then you need to call `.connect`.

The `HTTP` transport does not require you to call `.connect`, even though you need to call `.listen` for a service. This is because it doesn't need to create a persistent connection, and just uses plain HTTP calls as a client.
{: .notice--info}

```js
client.connect(function (err) {
  if (err) {
    console.error('There was an error connecting:', err)
  }
})
```

### 7. Use the client!

Now all of our setup is done, we can call our echo method.

```js
client.call('test', 'echo', 'test data', function (err, response) {
  console.log(err)      // -> undefined
  console.log(response) // -> 'test data'
})
```
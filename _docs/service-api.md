---
title: Service API
permalink: /docs/service/api/
---

## Instantiation

### `new Service([ transport, ... ])`

Passing an optional transport to this service is equivalent to calling `Service.addTransport`

## Instance Methods

### `Service#addTransport(transport[, callback])`

`Service.addTransport` takes an instance of a transport as the first argument, and an optional callback as the second.

If the service is currently listening, as soon as the transport has been added, it will start listening too.
{: .notice--info}

If you pass a callback, it will be called when the transport has been added.

### `Service#on(method, [schema,] fn)`

`Service.on` takes a method, an optional schema, and a callback.

Although passing in a schema is optional, it is <b>highly</b> recommended.
{: .notice--info}

### `Service#before(fn[, options])`

`Service.before` adds a function that will get executed **before** the function for each method gets called.

The optional options object can have the following properties.

| Name   | Type   | Example         | Description                                             |
|--------|--------|-----------------|---------------------------------------------------------|
| method | string | "reverseString" | Restrict this middleware to only the call for *method*. |

### `Service#after(fn[, options])`

`Service.after` adds a function that will get executed **after** the function for each method gets called.

The optional options object can have the following properties.

| Name   | Type   | Example         | Description                                             |
|--------|--------|-----------------|---------------------------------------------------------|
| method | string | "reverseString" | Restrict this middleware to only the call for *method*. |

### `Service#listen([callback])`

`Service.listen` will make all transports start listening for requests. 

`callback` will be called on when all transports are listening, or with an optional error if something went wrong.

### `Service#stop([callback])`

`Service.stop` will make all transports stop listening for requests.

`callback` will be called on when all transports are not listening aynmore, or with an optional error if something went wrong.

### `Service#call(method[, data], callback)`

`Service.call` allows you to call a method on **this** service, bypassing transports all together.

Its signature is the same as `Client.call` without `service`.

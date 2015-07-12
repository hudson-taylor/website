---
layout: docs
title: HT Express
description: 
permalink: /docs/utils/ht-express/
---

# HT Express

<a href="https://npmjs.org/package/ht-express"><img src="https://img.shields.io/npm/v/ht-express.svg"></a>
<a href="https://coveralls.io/r/hudson-taylor/ht-express"><img src="https://coveralls.io/repos/github/hudson-taylor/ht-express/badge.svg?branch=master"></a>
<a href="https://npmjs.org/package/ht-express"><img src="https://img.shields.io/npm/dm/ht-express.svg"></a>

Express middleware for routing requests to HT services. Using this allows you to serve a HTTP API using strictly defined and documentable methods.

## hte(client, service, method[, data]);

Where *client* is an instance of *ht.Client* that **has already been connected**.

Where *service* is the name of the service you wish to call.

Where *method* is the name of the method you wish to call.

Where *data* is an array of keys that will be merged from **req** into the data passed to the call. **Defaults to:** `[ 'body' ]`

### Validation errors

If the data collection from a request does not match the schema for a method, the HTTP response code will be set to 400, and the body of the response will be the validation error message.

### Special Response Keys

Returning an object with one of these keys from a method will make the HTTP response behave differently. See the table below.

| Name        | Type   | Description                   |
|-------------|--------|---------
| statusCode  | number | If the response from a service is an object, and has a key statusCode that is a number, the HTTP response code will be set to that value. This key will then be removed from the response. |

### Example

```js
var express = require('express');
var ht      = require('hudson-taylor');
var hte     = require('ht-express');
var s       = require('ht-schema');

// Create a new Local HT service
var transport = new ht.Transport.Local();
var service = new ht.Service(transport);
var client = new ht.Client({
  service: transport
});

// Add a method for the service
service.on("sayHello", s.String(), function(data, callback) {
  var response = 'Hello ' + data;
  return callback(null, response);
});

// Create a new express app
var app = express();

// Mount the service method on a url
app.get('/sayhello', hte(client, 'service', 'sayHello'));

// If you hit /sayHello with a string as a json body
// you will get a response that says 'Hello {body}'!
```

---
layout: docs
title: HT Decorators
description: 
permalink: /docs/utils/ht-decorators/
---

# HT Decorators

<a href="https://npmjs.org/package/ht-decorators"><img src="https://img.shields.io/npm/v/ht-decorators.svg"></a>
<a href="https://coveralls.io/r/hudson-taylor/ht-decorators"><img src="https://coveralls.io/repos/github/hudson-taylor/ht-decorators/badge.svg?branch=master"></a>
<a href="https://npmjs.org/package/ht-decorators"><img src="https://img.shields.io/npm/dm/ht-decorators.svg"></a>

ES7 Decorators that provide useful functionality for HT.

<blockquote class="ht-callout ht-callout-warning">
  <p>
    <b>Because of javascript limitations (read: hoisting), ES7 decorators can only be used on classes and class methods.</b>
  </p>
</blockquote>

## Expose

The expose decorator takes a HT service, and then mounts the class method so it is callable.

### @expose(service[, schema])

Where *service* is an instance of *ht.Service*
Where *schema* is a ht compatible schema.

### Example

```js
class methods {
  @expose(service, s.String());
  echo(data, callback) {
    return callback(null, data);
  }
}

// we need to instantiate an instance so
// our decorators get called.
new methods(); 

client.call("service", "echo", "hello world", function(err, response) {
  console.log(response); // "hello world"
});
```

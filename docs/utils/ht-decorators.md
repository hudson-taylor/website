---
layout: docs
title: HT Decorators
description: 
permalink: /docs/utils/ht-decorators/
---

<blockquote class="ht-callout ht-callout-warning">
  <p>
    <b>Because of javascript limitations (read: hoisting), ES7 decorators can only be used on classes and class methods.</b>
  </p>
</blockquote>

# Expose

The expose decorator takes a HT service, and then mounts the class method so it is callable.

### @expose(service)

Where *service* is an instance of *ht.Service*

### Example

```js
class methods {
  @expose(service)
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
---
layout: docs
title: Using HT Schema
description: 
permalink: /docs/schemas/overview/
---

# Schema

## Instance Methods

### Schema.validate(data)

Calling will try to validate *data*, and return the result.

### Schema.clone([object|array,])

Clone creates a copy of the schema.

<blockquote class="ht-callout ht-callout-info">
  <p>
    <b>Note:</b> You can pass more than one value to this function, they will be evaluated left to right.
  </p>
</blockquote>

If you pass an object as an argument to clone, it will merge your object with the schemas 'args', allowing you to set new attributes.

(**Object** only) If you pass an array as an argument, it will use the array values as a whitelist, and return a new Object schema with only these keys.

Replacing *args*:

```js

var schema = s.String({ opt: false });

schema.validate(); // this will throw

var newSchema = schema.clone({ opt: true });

newSchema.validate(); // this won't

```

Trimming an *object*:

```js

var schema = s.Object({
    a: s.Number(),
    b: s.Number()
});

schema.validate({
    a: 5,
    b: 5
});

var newSchema = schema.clone([ 'a' ]); // only return a

newSchema.validate({
    a: 5,
    b: 5 // < doesn't exist in this schema!
});

```
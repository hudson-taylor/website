---
layout: docs
title: HT Schema Overview
description: 
permalink: /docs/schemas/overview/
---

# Schema

Hudson Taylor supports adding schemas to both incoming, and outgoing data. Doing this lets you have peace of mind about the data you're going to be processing, and also lets you automatically generate documentation for methods!

<blockquote class="ht-callout ht-callout-info">
  <p>
    <b>Note:</b> you do not have to use <i>ht-schema</i> for schemas, you can use <a href="https://github.com/hudson-taylor/ht-joi">joi</a>, <a href="https://github.com/hudson-taylor/ht-tv4">JSON schema</a> or even write your own!
  </p>
</blockquote>

<blockquote class="ht-callout ht-callout-warning">
  <p>
    <b>Warning:</b> as of <b>3.0.0</b> ht-schema will no longer automatically wrap child objects with <b>s.Object</b>
  </p>
</blockquote>

## Instance Methods

### Schema.validate(data[, callback])

Calling will try to validate *data*.

A callback is optional and should take the signature of `function(err, data)`.

If no callback is passed, this method will return the validated data, or it will throw.

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
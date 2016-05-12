---
title: "HT Schema"
permalink: /docs/schemas/overview/
---

{% include base_path %}

[![Build Status](https://travis-ci.org/hudson-taylor/ht-schema.svg?branch=master)](https://travis-ci.org/hudson-taylor/ht-schema)
[![Coverage Status](https://img.shields.io/coveralls/hudson-taylor/ht-schema.svg)](https://coveralls.io/r/hudson-taylor/ht-schema)

Hudson Taylor supports adding schemas to both incoming, and outgoing data. Doing this lets you have peace of mind about the data you're going to be processing, and also lets you automatically generate documentation for methods!

**Protip:** you do not have to use *ht-schema* for schemas, you can use [Joi](https://github.com/hudson-taylor/ht-joi), [JSON Schema](https://github.com/hudson-taylor/ht-tv4) or even write your own bindings to another validation library!
{: .notice--info}

## Installation

Although `ht-schema` is not bundled with Hudson-Taylor by default, it is highly recommended that you use it.

To install:

```
npm install ht-schema --save
```

## Using `ht-schema` with Hudson Taylor

Hudson Taylor has built-in support for `ht-schema`, you can utilize it by passing a schema object as the second argument to a `service.on` call.

### Example

```js
var schema = s.Object({
  numberOne: s.Number(),
  numberTwo: s.Number()
})

service.on('echo', schema, ...)
```

## Using `ht-schema` standalone

You can also use this library as a standalone validation library!

Each validator has a `validate` method that will either return data if the validation passes, or will throw if it fails.

### Example

```js
var schema = s.Number()

var out = schema.validate(5)

console.log(out) // 5

schema.validate('hello') // throws
```

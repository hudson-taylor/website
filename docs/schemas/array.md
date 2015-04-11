---
layout: docs
title: Array Validator
description: 
permalink: /docs/schemas/array/
---

# s.Array([options,] validators)

The array validator lets you specify a number of validators that each item in the array can match.

## Example

```js

var schema = s.Array([
  // each item in the array can
  // either be a String, or Number
  s.String(),
  s.Number()
]);

schema.validate([ 42, 'hello world' ]);

```

## Options

### opt: Boolean

Passing opt will make any data for this schema optional.

### length: Number

Require data to have exactly *n* elements.

### minLength: Number

Require data to have a length of at least *n*.

### maxLength: Number

Require data to have a maximum length of *n*.
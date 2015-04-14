---
layout: docs
title: TypedArray Validator
description: 
permalink: /docs/schemas/typedarray/
---

# s.TypedArray([options,] validators)

The typed array validator lets you specify an array of validators. Each element in the array validated has to explicitly match the validator in the same index position.

<blockquote class="ht-callout ht-callout-info">
  <p>
    This validator will also fail if the data has a different length to the number of validators passed.
  </p>
</blockquote>

## Example

```js

var schema = s.TypedArray([
  s.String(),
  s.Number()
]);

// this will pass
schema.validate([ 'hello world', 42 ]);

// this will not pass TypedArray, even though it would pass Array
schema.validate([ 42, 'hello world' ]);

```

## Options

### opt: Boolean

Passing opt will make any data for this schema optional.

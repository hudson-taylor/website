---
layout: docs
title: Object Validator
description: 
permalink: /docs/schemas/object/
---

# s.Object([options,] validators)

The object validator lets you nest other schemas.

## Example

```js

var schema = s.Object({ strict: false }, {
  key:  s.String(),
  many: s.Number()
});

schema.validate({
  key: "hello",
  many: 5,
  other: "key" // strict is false, so we can pass other keys
});

```

## Options

### opt: Boolean

Passing opt will make any data for this schema optional.

### strict: Boolean

If false, keys not specified in *validators* will not cause checking to fail.


## Common child options

### default: <value based on type of child>

All child validators of an object also support a default value.
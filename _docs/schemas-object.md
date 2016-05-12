---
title: "Schema validator - Object"
permalink: /docs/schemas/object/
---

Validates input is an object, and recurses child keys and verifies those keys pass validation checks too.

## Example

This example creates a non-strict object validator. It has accepts two keys, `key` and `many` - both with strict types. When we validate we also pass `other` which is not in the schema, but because `strict` is set to `false` we just pass that value through without any other checking.

```js
var schema = s.Object({ strict: false }, {
  key: s.String(),
  many: s.Number()
})

schema.validate({
  key: "hello",
  many: 5,
  other: "key" // strict is false, so we can pass other keys
})
```

## Options

### Optional

```
{ opt: Boolean }
```

### Strict

Make this validator accept undefined as a value.

```
{ strict: Boolean }
```

If false, keys not specified in *validators* will not cause checking to fail.

## Common child options

### Default Values

Setting the key `default` will default to that value if no value is passed, and the child validator is optional (`opt: true`)

```js
var schema = s.Object({
  key: s.String({ opt: true, default: "hello world" })
})

var output = schema.validate({ key: undefined })

console.log(output.key) // "hello world"
```

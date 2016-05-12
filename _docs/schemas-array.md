---
title: "Schema validator - Array"
description: 
permalink: /docs/schemas/array/
---

Validates each item in an array matches one of the schemas you provide.

**Warning:** If you want to check that each item matches a **specific** validator, take a look at [TypedArray](/docs/schemas/typedarray/) instead 
{: .notice--warning}

## Example

```js
var schema = s.Array({ length: 2 }, [
  // Require each item in the array to be either
  // a number, or a boolean, in no particular order.
  s.Number(),
  s.Boolean()
])

var output = schema.validate([ true, 42 ])

console.log(output) // [ true, 42 ]
```

## Options

### Optional

```
{ opt: true }
```

Make this validator accept undefined as a value.

### Strict Length

```
{ length: Number }
```

Require data to have exactly *n* elements.

### Minimum Length

```
{ minLength: Number }
```

Require data to have a length of at least *n*.

### Maximum Length

```
{ maxLength: Number }
```

Require data to have a maximum length of *n*.

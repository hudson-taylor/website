---
title: "Schema validator - TypedArray"
description: 
permalink: /docs/schemas/typedarray/
---

The typed array validator lets you specify an array of validators. Each element in the array validated has to explicitly match the validator in the same index position.

**Warning:** This validator will also fail if the data has a different length to the number of validators passed.
{: .notice--warning}

## Example

```js
var schema = s.TypedArray([
  s.String(),
  s.Number()
]);

// this will pass
schema.validate([ 'hello world', 42 ]);

// this will not pass TypedArray, even though it would pass Array
// as we explicitly require the first element to be a string.
schema.validate([ 42, 'hello world' ]);
```

## Options

### Optional

```
{ opt: true }
```

Make this validator accept undefined as a value.

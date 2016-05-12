---
title: "Schema validator - Date"
permalink: /docs/schemas/date/
---

Validate input is a valid Date

## Options

### Optional

```
{ opt: true }
```

Passing opt will make any data for this schema optional.

### Minimum Date

```
{ min: Date }
```

The date passed must be at least this time.

### Maximum Date

```
{ max: Date }
```

The date passed must be less than this time.

### Parse Value

```
{ parse: Boolean }
```

Try and parse the data into a Date before validating.


**Warning:** *parse* can result in unusual behavior when combined with the **Array** and **TypedArray** validators. See code example below.
{: .notice--warning}

```js
// The Array validator tries to validate things left-to-right
// so in this case if anything matches s.Date it will stop.
// Because s.Date has the parse option set it will try and
// parse numbers as epoch times and return a date.
var schema = s.Array([ s.Date({ parse: true }), s.Number() ]);
var result = schema.validate([ 5 ]);
// result -> [ Thu Jan 01 1970 10:00:00 GMT+1000 (AEST) ]
```

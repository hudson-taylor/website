---
layout: docs
title: Date Validator
description: 
permalink: /docs/schemas/date/
---

# s.Date([options])

## Options

### opt: Boolean

Passing opt will make any data for this schema optional.

### min: Date

The date passed must be at least this time.

### max: Date

The date passed must be less than this time.

### parse: Date

Try and parse the data into a Date before validating.

<blockquote class="ht-callout ht-callout-warning">
  <p>
    <b>Warning:</b> <i>parse</i> can result in unusual behavior when combined with the <b>Array</b> validator. See code example below.
  </p>
</blockquote>

```js
// The Array validator tries to validate things left-to-right
// so in this case if anything matches s.Date it will stop.
// Because s.Date has the parse option set it will try and
// parse numbers as epoch times and return a date.
var schema = s.Array([ s.Date({ parse: true }), s.Number() ]);
var result = schema.validate([ 5 ]);
// result -> [ Thu Jan 01 1970 10:00:00 GMT+1000 (AEST) ]
```

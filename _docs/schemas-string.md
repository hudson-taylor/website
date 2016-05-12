---
title: "Schema validator - String"
description: 
permalink: /docs/schemas/string/
---

Validates input is a string.

## Options

### Optional

```
{ opt: true }
```

Make this validator accept undefined as a value.

### Strict Length

```
{ len: Number }
```

Require the string to be a specific length.

### Minimum Length

```
{ min: Number }
```

Require the string to be a minimum length.

### Maximum Length

```
{ max: Number }
```

Require the string to be a maximum length.

### Trim Value

```
{ trim: Boolean }
```

Trim the string returned.

### Coerce to lowercase

```
{ lower: Boolean }
```

Convert the string to lowercase.

### Coerce to uppercase

```
{ upper: Boolean }
```

Convert the string to uppercase.

### Match regex

```
{ regex: Regex }
```

Require string to match regex.

### Require value from enum

```
{ enum: Array<String> }
```

Require the string to match any of the values in the array.

### Sanitize Value

```
{ sanitize: Boolean }
```

Escape data returned.

---
layout: docs
title: String Validator
description: 
permalink: /docs/schemas/string/
---

# s.String([options])

## Options

### opt: Boolean

Passing opt will make any data for this schema optional.

### len: Number

Require the string to be a specific length.

### min: Number

Require the string to be a minimum length.

### max: Number

Require the string to be a maximum length.

### trim: Boolean

Trim the string returned.

### lower: Boolean

Convert the string to lowercase.

### upper: Boolean

Convert the string to uppercase.

### regex: Regex

Require string to match regex.

### enum: Array<string>

Require the string to match any of the values in the array.

### sanitize: Boolean

Escape data returned.

---
layout: docs
title: Custom Validator
description: 
permalink: /docs/schemas/custom/
---

# Schema.makeValidator(name, fn)

Calling *s.makeValidator* will return an instance of a **Validator**.

The *name* you pass to this validator will only be used for documentation purposes, you can assign the result to any variable name and use that as you wish.

The *fn* you pass needs to take the following 3 arguments:

<blockquote class="ht-callout ht-callout-info">
  <p>
    <b>args</b> and <b>childValidators</b> are defined when you call the validator (not when you call makeValidator)
  </p>
</blockquote>

##### args

This argument is an object of options that are passed into the validator.

You can use this argument to turn different features on and off for a validator.

<blockquote class="ht-callout ht-callout-warning">
  <p>
    Even though using <i>args</i> is optional, it is <b>highly</b> recommended that you support '<b>opt</b>'.
  </p>
</blockquote>

```js
s.String({ opt: true }); // { opt: true } are 'args' in this example
```

##### childValidators

This argument is either an array, or an object, and will consist of other Validators.

By using this argument you can implement validators like **Object**, **Array** and **TypedArray**.

```js
s.Array({ opt: true }, [ s.String() ]); // [ s.String() ] are 'childValidators' in this example
```

##### data

This argument is the actual data you need to validator and parse.

```js
var schema = s.String();
schema.validate("hello"); // hello is 'data' here
```

The *fn* you pass needs to do one of two things:

* If the data does not pass your expectations - throw an error
* If the data does pass - return the value you wish to be passed back

If you wish to not return anything, or remove this validator from a parent schema (**Object** etc) you can return the value of

```js
require("ht-schema/lib/deleteKey")
```

# Example

We're going to implement a very basic 'String' validator.

```js

// First we have to call makeValidator with a name, and a function.
var stringValidator = s.makeValidator("String", function(args, childValidators, data) {
  
  // First, we should check that we actually have data
  if(data === undefined) {
    // It's highly recommended that all validators support
    // handling the 'opt' argument. If it's true, we shouldn't
    // throw if we don't get any data.
    if(args.opt) {
      // Ideally we would require this above.
      return require("ht-schema/lib/deleteKey");
    }
    // opt is not set, so we have to throw
    throw new Error("oops, you didn't pass a String!");
  }

  // Check if the type of data is correct
  if(typeof data !== "string") {
    // throw an error if it's not!
    throw new Error("expected String, got:" + typeof data);
  }

  // Everything is fine, return the data!
  return data;

});

// Now that we have a validator, we can call validate.
var result = stringValidator.validate("hello world"); // "hello world"
```

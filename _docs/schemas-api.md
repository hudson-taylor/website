---
title: "HT Schema - API"
permalink: /docs/schemas/api/
---

## Exported Methods

### `htSchema.makeValidator(name, fn)`

See [Writing a custom validator](/docs/schemas/custom/)

### `htSchema.generate(json)`

This method will generate a schema from the result of `Validator#document()`. This allows you to save schemas, and load them at will.

## Validator methods

### `Validator#validate(data[, key, callback])`

The validate method calls the internal validators and ensures the data you pass matches the schema.

*key* should be passed if the schema is being validated as a child of aonther validator to ensure messages have the correct context.

A callback is optional and should take the signature of `function(err, data)`.

If no callback is passed, this method will return the validated data, or it will throw.

### `Validator#document()`

Calling document will return a blob of JSON, this content will contain the necessary configuration for regenerating a schema with *#htSchema.generate*. This allows you to store schemas as JSON, and even means you can remotely load them over the network.

```js

var schema = s.Object({
  hello: s.String({ opt: true }).comment("this is the hello key")
})

console.log(schema.document())

/*
{ name: 'Object',
  args: {},
  children:
   { hello:
      { name: 'String',
        args: { opt: true },
        comment: 'this is the hello key' } } }
*/

```

### `Validator#comment(String|Function)`

Calling this function will add a message to the schema for use with `Validator#document()`.

### `Validator#clone([object|array,])`

Clone creates a copy of the schema.


**Note:** You can pass more than one value to this function, they will be evaluated left to right.
{: .notice--info}

If you pass an object as an argument to clone, it will merge your object with the schemas 'args', allowing you to set new attributes.

**Note:** (`Object` only) If you pass an array as an argument, it will use the array values as a whitelist, and return a new Object schema with only these keys.
{: .notice--info}

Replacing `args`:

```js
var schema = s.String({ opt: false })

schema.validate() // this will throw

var newSchema = schema.clone({ opt: true })

newSchema.validate() // this won't
```

Trimming an *object*:

```js

var schema = s.Object({
  a: s.Number(),
  b: s.Number()
})

schema.validate({
  a: 5,
  b: 5
})

var newSchema = schema.clone([ 'a' ]) // only return a

newSchema.validate({
  a: 5,
  b: 5 // < doesn't exist in this schema!
})
```

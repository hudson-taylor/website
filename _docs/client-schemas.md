---
title: Client - Schemas
permalink: /docs/client/schemas/
---

Adding schemas to your client accomplishes the opposite of schemas for service methods, you can use them to validate the response from a service.

## Adding client schemas

See `Client#addSchema` in the [API Docs](/docs/client/api/) for function signature.

## Example

```js
var schema = s.Object({
  username: s.String(),
  password: s.String()
})

// Note, it's possible to add a schema here that
// differs from what the remote service is expecting
// the schema to be.
client.addSchema("user", "login", schema)

client.call("user", "login", "hello world", function(err) {
  console.log(err.error); // -> "Got string, required Object"
  console.log(err.$htValidationError); // -> true
})
```

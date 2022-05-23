---
title: Update project information
description: 'The API has a helper function to receive all valid project keys/properties which can be set by an external client'
position: 3
category: 'Updating data'
fullscreen: 'true'
---

The API has a helper function to receive all valid project keys/properties which can be set by an external client:

**Helper function - get valid project keys** <badge>Since: 0.1</badge>

```js
URI: https://<im4>/project/{projectId}/keys
```

**Request-type:** `GET`  
**Parameters:** `{projectId}` - (part of URI) `ID` of the project

**Return data:**

```js
{[key] => (
    [comment] => Comment on key
    [read] => Readable key
    [write] => Writable key
), ... }
```

Fetches an array of valid `keys` / `properties` for a project which can be set or retrieved.

<alert> Note: every property comes with a comment and a flag if it is readable and/or writeable.
</alert>

The general function for updating keys/properties on a project, accepts a JSON array with key - value-pairs:

**Update project keys/properties** <badge>Since: 0.1</badge>

```js
URI: https://<im4>/project/{projectId}
```

**Request-type:** `POST`  
**Parameters:** `{data}`: `JSON`  
**Return data:** HTTP 200 on success

Sets properties for given projectId. Data given as a `JSON` array (`key` => `value`).

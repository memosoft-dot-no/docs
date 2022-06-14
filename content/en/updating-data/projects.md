---
title: Projects
description: ''
position: 21
category: 'Updating data'
---

## Create new project

```js
URI: https://<im4>/project
```

- **Request-type:** `POST`
- **Parameters:** `{data}`: `JSON`
- **Return data:**
  `{projectId}` `(integer)`

Creates a new project and returns `project-id`. Data must be provided as a `JSON` array. <br>
Required fields are `subject_firstname` and `subject_lastname`.
Any other [valid project key](/project-keys) can be specified as well.

## Update project keys/properties

```js
URI: https://<im4>/project/{projectId}
```

- **Request-type:** `POST`
- **Parameters:** `{data}`: `JSON`
- **Return data:** HTTP 200 on success

Sets properties for given project with specified `projectId`. Data given as a `JSON` array (`key` => `value`).
<br>See list of all [valid project keys here](/project-keys).


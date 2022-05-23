---
title: Create new project
description: 'External systems can create new projects for the agency. Required data are the first- and last name for the project, but any other valid project key can be specified in the JSON input parameters.'
position: 2
category: 'Updating data'
fullscreen: 'true'
---

External systems can create new projects for the agency. Required data are the first- and last name for the project, but any other valid project key can be specified in the JSON input parameters.

**API: Create new project** <badge>Since: 0.1</badge>

```js
URI: https://<im4>/project
```

**Request-type:** `POST`

**Parameters:**

- `{data}`: `JSON`

**Return data:**

- `{project-id}` `(integer)`

Creates a new project and returns `project-id`. Data must be provided as a `JSON` array. Required fields are `subject_firstname` and `subject_lastname`. Any other valid project key can be specified as well (see [Helper function](/updating-data/file-uploading#helper-functions)).

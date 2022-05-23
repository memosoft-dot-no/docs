---
title: Project files
description: ''
position: 22
category: App specific information
badge: 'Since 0.21'
---

## Delete files in project

```js
URI: https://<im4>/project/{projectId}/files/{file_ids}
```

- **Request-type:** `DELETE`
- **Parameters:**
  - `{projectId}` - (part of URI) ID of the project
  - `{file_ids}`: (part of URI) File ids to delete
- **Return data:** Array of actual deleted files (files not deleted if used in any product)

Delete list of files from project

## Run color preset on files

```js
URI: https://<im4>/project/{projectId}/files/{file_ids}/pfc-apply/{preset}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{projectId}` - (part of URI) ID of the project
  - `{file_ids}`: (part of URI) File ids to delete
  - `{preset}`: (part of URI) Default or agency preset or ‘clear’
- **Return data:** HTTP 200 on success

Add specified files to background job for enhancing image. Loading files from project while files in queue or processing includes information about what files are queued and what queue they are currently in.

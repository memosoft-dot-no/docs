---
title: Project details
description: ''
position: 41
category: Fetching data
---

### Fetch available projects
Fetche list of projects – if user has access to multiple agencies – projects in all agencies will be returned unless `agency_id` is specified <br>

```js
URI: https://<im4>/projects/{agency_id?}
?days={days?}
?search={search?}
?take={take?}&skip={skip?}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{agency_id}` (part of URI) (optional): Agency - fallback to client agency
  - `{days}` (integer) (default 120): Days to include - skipped if search/take set
  - `{search}` (string): Multi-word search – if specified days is ignored.
  - `{take}` (integer): <badge>Since 0.19</badge> Limit result – used for paging – if specified days is ignored.
  - `{skip}` (integer): <badge>Since 0.19</badge> Skip first x results – used for paging – will only work if take specified
- **Return data:**
  `{mixed}` `(JSON)`

### Fetch all project details
Fetche all project info (as defined in [valid project keys](/project-keys)) as `JSON` data.

```js
URI: https://<im4>/project/{projectId}
```

- **Request-type:** `GET`
- **Parameters:** `{projectId}` (part of URI): `ID` of the project
- **Return data:** ` {project}` `(JSON)`

### Fetch specific project details

Fetch project data as `JSON` - either the entire data set, a specific key, or a set of comma separated keys (see list of [valid project keys](/project-keys))

```js
URI: https://<im4>/project/{projectId}/{key|keys}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{projectId}` (part of URI): ID of the project
  - `{key}` (part of URI): valid project key to be fetched
  - `{keys}`<badge>Since 0.8</badge> (part of URI): valid comma separated project keys to be fetched
- **Return data:**
  `{mixed}` `(JSON)`
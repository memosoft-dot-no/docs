---
title: Proofreading information
description: 'Fetch available proofreadings'
position: 13
category: Fetching data
fullscreen: 'true'
---

### Fetch available proofreadings

```js
URI: https://<im4>/proofreading_batches/{agency_id?}
?days={days?}
?search={search?}
?take={take?}&skip={skip?}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{days}` – Defaults to 120 days if not specified – skipped if search/take set
  - `{search}` – Multi-word search – if specified days is ignored.
  - `{take}` – Limit result – used for paging – if specified days is ignored
  - `{skip}` – Skip first x results – used for paging – will only work if skip specified
  - `{agency_id}`
- **Return data** `{mixed}` `(JSON)`

Fetches list of proofreadings batches - if user has access to multiple agencies – `proofreading_batches` in all agencies will be returned unless `agency_id` is specified  
<badge>Since 0.14</badge>

#### Fetch project proofreadings batches

`proofreading_batches` is a valid key on projects, so get through project:

```js
/project/{projectId}/proofreading_batches
```

#### Fetch a specific full proofreading batch

Get through project:

```js
/project/{projectId}/proofreading_batch/{batchId}
```

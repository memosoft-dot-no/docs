---
title: Proofreadings
description: ''
position: 43
category: Fetching data
badge: 'Since 0.14'
---

## Proofreadings

When a product is almost finished a proofreading can be sent to get an approval before an order is made.
Several proofreadings can be sent to different recipients and in total they make up a proofreading batch.

### Fetch proofreading batches

Fetch list of proofreading batches - if user has access to multiple agencies – `proofreading_batches` in all agencies will be returned unless `agency_id` is specified <badge>Since 0.14</badge>

```js
URI: https://<im4>/proofreading_batches/{agency_id?}
?days={days?}
?search={search?}
?take={take?}&skip={skip?}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{agency_id}` (part of URI) (optional): Agency - fallback to client agency
  - `{days}` (integer) (default 120): Days to include - skipped if search/take set
  - `{search}` (string): Multi-word search – if specified days is ignored.
  - `{take}` (integer): Limit result – used for paging – if specified days is ignored.
  - `{skip}` (integer): Skip first x results – used for paging – will only work if take specified
  
- **Return data** `{mixed}` `(JSON)`


### Fetch project proofreadings batches

`proofreading_batches` is a [valid key](/project-keys) on projects, so get through project:

```js
/project/{projectId}/proofreading_batches
```

### Fetch a specific full proofreading batch

Get a specific proofreading batch with additional information (see proofreading batch table and proofreading table [here](/project-keys) 

```js
/project/{projectId}/proofreading_batch/{batchId}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{projectId}` (part of URI): Project ID
  - `{batchId}` (part of URI): Proofreading batch ID

- **Return data** `{mixed}` `(JSON)`


---
title: Order information
description: 'Fetch available orders'
position: 42
category: Fetching data
fullscreen: 'true'
badge: 'Since 0.12'
---

### Fetch available orders

```js
URI: https://<im4>/orders/{agency_id?}
days={days?}
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

Fetches list of orders - if user has access to multiple agencies – orders in all agencies will be returned unless agency_id is specified

#### Fetch project orders

`orders` is a valid key on projects, so get through project:

```js
/project/{projectId}/orders
```

#### Fetch a specific full order

Get through project:

```js
/project/{projectId}/order/{orderId}
```

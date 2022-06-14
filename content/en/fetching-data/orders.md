---
title: Orders
description: ''
position: 44
category: Fetching data
badge: 'Since 0.12'
---

## Orders

When product is finished an order is made - both if printed product or a digital service.

### Fetch available orders

Fetch list of orders - if user has access to multiple agencies – orders in all agencies will be returned unless agency_id is specified

```js
URI: https://<im4>/orders/{agency_id?}
days={days?}
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

#### Fetch project orders

`orders` is a [valid key](/project-keys) on projects, so get through project:

```js
/project/{projectId}/orders
```

#### Fetch a specific full order

Get a specific order with additional information (see ordertable [here](/project-keys)

```js
/project/{projectId}/order/{orderId}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{projectId}` (part of URI): Project ID
  - `{orderId}` (part of URI): Order ID

- **Return data** `{mixed}` `(JSON)`


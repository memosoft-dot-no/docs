---
title: Design archive
description: 'Fetch available designs for agency'
position: 43
category: Fetching data
fullscreen: 'true'
badge: 'Since 0.24'
---

### Fetch all available designs for agency

```js
URI: https://<im4>/designs
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

Fetches list of all available designs. Both global and all designs agency has acl access to.
Continue reading to find information about how to create a local cache of designs

<badge>Since 0.4</badge>

`/designs` request above give all designs agency has access to, but If implementing a global local cached of designs this list of designs cannot be served for all agencies.
In that case – load /global once and /acl per agency and store in cache.

Concatenation of global list and an agencies acl list gives the same result as the /designs request. This way designs can be cached e.g. once each night and then no requests needed to get designs through API untnil next night

### Fetch all designs without acl restrictions

```js
URI: https://<im4>/designs/global
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

Fetches list of all global design – all designs with no acl restrictions.

<badge>Since 0.24</badge>

### Fetch all designs with acl restrictions and where agency passes these restrictions

```js
URI: https://<im4>/designs/acl
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

Fetches list of all designs where acl restrictions is set and where agency passes these restrictions.

<badge>Since 0.24</badge>

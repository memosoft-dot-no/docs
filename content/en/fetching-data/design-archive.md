---
title: Design archive
description: ''
position: 45
category: Fetching data
badge: 'Since 0.24'
---

## Designs

A design is a background used in a printed product. **app** includes a big archive with categorized and tagged designs.

### Fetch all designs for agency

Fetches list of all available designs. Both global and all designs agency has `acl` access to.
Continue reading to find information about how to create a local cache of designs

<badge>Since 0.4</badge>

```js
URI: https://<im4>/designs
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

<alert>`/designs` request give all designs agency has access to, but if client is implementing a global cache of designs this list of designs cannot be served for all agencies.<br><br>In that case – load /global once and /acl per agency and store in cache. <br><br>Concatenation of global list and an agencies acl list gives the same result as the /designs request. This way designs can be cached e.g. once each night and then no requests needed to get designs through API untnil next night </alert>

### Fetch all global designs

Fetch list of all global design – all designs with no acl restrictions. <badge>Since 0.24</badge>

```js
URI: https://<im4>/designs/global
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

### Fetch all restricted designs available for agency

Fetch list of all designs where acl restrictions is set and where agency passes these restrictions. <badge>Since 0.24</badge>

```js
URI: https://<im4>/designs/acl
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`


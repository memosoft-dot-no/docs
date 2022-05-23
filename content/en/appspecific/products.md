---
title: Project products
description: ''
position: 21
category: App specific information
badge: 'Since 0.16'
---

## Fetch available products on project

```js
URI: https://<im4>/project/{projectId}/products
```

- **Request-type:** `GET`
- **Parameters:** `{projectId}` - (part of URI) `ID` of the project
- **Return data:** `{mixed}` `(JSON)`

Fetches list of products on a specific project. Both documents and services.

## Fetch document preview

```js
URI: https://<im4>/doc/{docId}/preview?etag={etag}&size={size}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{docId}` - (part of URI) ID of the document
  - `{size}` - size of requested preview
  - `{etag}` - key changed each time doc is changed
- **Return data:** `(image/jpeg}` - bitmap data

Fetch document preview in specified size

## Fetch service preview

```js
URI: https://<im4>/service/{serviceId}/preview?etag={etag}&size={size}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{serviceId}}` - (part of URI) ID of the service
  - `{size}` - size of requested preview
  - `{etag}` - key changed each time doc is changed
- **Return data:** `(image/jpeg}` - bitmap data

Fetch service preview in specified size

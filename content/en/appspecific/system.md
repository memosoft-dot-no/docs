---
title: System
description: ''
position: 26
category: App specific information
---

## Get translations

```js
URI: https://<im4>/translations
```

- **Request-type:** `GET`
- **Parameters:** `category` (string): Optional
- **Return data:** `{mixed}` `(JSON)`

Fetch array of codes and translation for server.  
Category ‘app’ is default, but if specified other translations can be loaded.  
<badge>Since 0.12</badge>

## Get pfc color presets

```js
URI: https://<im4>/pfc/presets/{agency_id}
```

- **Request-type:** `GET`
- **Parameters:** `agency_id` (int)
- **Return data:** `{mixed}` `(JSON)`

Fetch array of available color presets for an agency  
<badge>Since 0.21</badge>

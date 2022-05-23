---
title: Events
description: ''
position: 24
category: App specific information
badge: 'Since 0.18'
---

## Get list of events available for user

```js
URI: https://<im4>/events
```

- Request-type: `GET`
- Parameters: `days` (int): Optional to reduce number of events
- Return data: `{mixed}` `(JSON)`

Fetch list of events from event-log available for current authenticated user.

## Get list of events for a specific project

```js
URI: https://<im4>/project/{projectId}/events
```

- Request-type: `GET`
- Return data: `{mixed}` `(JSON)`

Fetch list of events from event-log available for current authenticated user.

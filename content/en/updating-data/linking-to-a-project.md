---
title: Linking to a project
description: 'There is two different ways for linking to a project'
position: 23
category: 'Updating data'
fullscreen: 'true'
---

There is two different ways for linking to a project:

**Link: Linking to a project – redirect user and user sign in with their own credentials** <badge>Since: 0.8</badge>

```js
URI: https://<im4>/iapi/projects/{projectId}/checkaccess/{clientid}
```

- **Request-type:** `GET`
- **Parameters:**  
  `{projectId}` - (part of URI) `ID` of the project  
  `{client_id}` (integer): `<given client id>`

Client id is included for security reasons. If user already have an im4 sesson running no credential page is shown – else user will be asked for credentials before access to project is checked and project is shown. If no access to project user is redirect `home`

**API: Magic linking – get magic-link through api and redirect – auto signed in** <badge>Since: 0.23</badge>

```js
URI: https://<im4>/project/{projectId}/magic-link?user={email}
```

- **Request-type:** `GET`
- **Parameters:** `{projectId}` - (part of URI) `ID` of the project

Api request is done including user email. If a user exist in im4 with exact same email and user has access to project then a magic link is returned. Redirect user to that magic link and user is automatically signed in. Magic link works only once

Link to project will normally only work if user is part of agency project is owned by or if agency is part of an agency group user is given access to. If user don’t have access to project, but agency is part of same agency group as users agency there is on last way to get access: If api client is granted access to modify users, access will automatically be given for user to access project agency projects.

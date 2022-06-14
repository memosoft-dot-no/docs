---
title: Linking to a project
description: ''
position: 12
category: 'General'
---

There is two different ways for linking to a project:

## Direct link
Linking to a project by redirecting user to a project URI and user sign in with their own credentials <badge>Since: 0.8</badge>

```js
URI: https://<im4>/iapi/projects/{projectId}/checkaccess/{clientid}
```

- **Request-type:** `GET`
- **Parameters:**  
  `{projectId}` (part of URI): `ID` of the project  
  `{client_id}` (integer): `<given client id>`

Client id is included for security reasons. If user already has an **app** session running no credential page is shown – else user will be asked for credentials before access to project is checked and project is shown. If no access to project user is redirected `home`

## Magic link
Request a magic project link through api and redirect user for auto sign in<badge>Since: 0.23</badge>

```js
URI: https://<im4>/project/{projectId}/magic-link?user={email}
```

- **Request-type:** `GET`
- **Parameters:** `{projectId}` (part of URI): `ID` of the project

Api request is done including user email. If a user exist in **app** with exact same email and user has access to specified project, a magic link is returned. Redirect user to that magic link and user is automatically signed in. Magic link works only once

Link to project will normally only work for users in the projects agency, or if the project agency is part of an agency group the user belongs to.<br><br> 
If api client has access to change users, access will automatically be given to users of agencies in the same agency group as the projects agency

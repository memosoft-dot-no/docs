---
title: Handling users
description: 'External API clients can have access to agency users'
position: 5
category: 'Updating data'
---

External API clients can have access to agency users.

### Get agency users

```js
URI: https://<im4>/agency/{agency}/users
```

**Request-type:** `GET`

**Parameters:**  
`{agency}` - (part of URI) `ID` of the agency

**Return data:**  
`{users}` `(JSON)`

Fetches an array of users for the given Agency.
<badge>Since: 0.5</badge>

### Create agency user

```js
URI: https://<im4>/agency/{agency}/user
```

**Request-type:** `POST`

**Parameters:**  
`{agency}` - (part of URI) ID of the agency

**Return data:**

- `{firstname}` - String, required
- `{lastname}` - String
- `{email}` - String, valid email, required, unique
- `{new_password}` - String, min 8 chars
- `{new_password_confirmation}` - same as new_passord

Creates new user for agency, and returns the user object.  
<badge>Since: 0.5</badge>

### Get agency user

```js
URI: https://<im4>/agency/{agency}/user/{user}
```

**Request-type:** `GET`  
**Parameters:**

- `{agency}` - (part of URI) ID of the agency
- `{user}` - (part of URI) ID of the user

**Return data:**

- `{user}` `(JSON)`

Fetches the user object. <badge>Since: 0.5</badge>

### Update agency user

```js
URI: https://<im4>/agency/{agency}/user/{user}
```

**Request-type:** `PATCH`

**Parameters:**

- `{agency}` - (part of URI) ID of the agency
- `{user} `- (part of URI) ID of the user

**Return data:**

- `{firstname}` - String, required
- `{lastname}` - String
- `{email}` - String, valid email, required, unique
- `{new_password}` - String, min 8 chars
- `{new_password_confirmation}` - same as `new_passord`

Updates given user, and returns updated user object. <badge>Since: 0.5</badge>

### Delete agency user

```js
URI: https://<im4>/agency/{agency}/user/{user}
```

**Request-type:** `DELETE`

**Parameters:**

- {agency} - (part of URI) ID of the agency
- {user} - (part of URI) ID of the user

**Return data:** `HTTP 200` on success

Deletes user for agency. <badge>Since: 0.5</badge>

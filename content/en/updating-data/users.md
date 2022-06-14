---
title: Users
description: ''
position: 23
category: 'Updating data'
---

External API clients can be given access to handle agency users.
Get list of users, add users, remove users and change user details and passwords.

### Get agency users

Fetch an array of users for the given Agency. <badge>Since: 0.5</badge>

```js
URI: https://<im4>/agency/{agency}/users
```

- **Request-type:** `GET`
- **Parameters:** `{agency}` (part of URI): `ID` of the agency
- **Return data:** `{users}` `(JSON)`

### Create agency user

Create a new user for agency, and returns the user object.<badge>Since: 0.5</badge>

```js
URI: https://<im4>/agency/{agency}/user
```

- **Request-type:** `POST`
- **Parameters:** `{agency}` - (part of URI) ID of the agency
- **Return data:**  
  `{firstname}` (string) (required) : Users first name  
  `{lastname}` (string): Users last name  
  `{email}` (string) (valid email, required, unique): Users email  
  `{new_password}` (string) (min 8 chars): Users password  
  `{new_password_confirmation}` (string): Same as new_passord


### Get agency user

Fetch a user object. <badge>Since: 0.5</badge>

```js
URI: https://<im4>/agency/{agency}/user/{user}
```

- **Request-type:** `GET`
- **Parameters:**
  `{agency}` (part of URI): ID of the agency
  `{user}` (part of URI): ID of the user
- **Return data:**
  `{user}` `(JSON)`

### Update agency user

Update given user, and return updated user object. <badge>Since: 0.5</badge>

```js
URI: https://<im4>/agency/{agency}/user/{user}
```

- **Request-type:** `PATCH`
- **Parameters:**  
  `{agency}` (part of URI): ID of the agency  
  `{user} ` (part of URI): ID of the user
  `{firstname}` (string) (required) : Users first name  
  `{lastname}` (string): Users last name  
  `{email}` (string) (valid email, required, unique): Users email  
  `{new_password}` (string) (min 8 chars): Users password  
  `{new_password_confirmation}` (string): Same as new_passord

- **Return data:**
  `{user}` `(JSON)`

### Delete agency user

Delete a user. <badge>Since: 0.5</badge>

```js
URI: https://<im4>/agency/{agency}/user/{user}
```

- **Request-type:** `DELETE`
- **Parameters:**  
  `{agency}` (part of URI): ID of the agency  
  `{user}` (part of URI): ID of the user
- **Return data:** `HTTP 200` on success

### Fetch agencies

Fetch list of all agencies in agency group. 

```js
URI: https://<im4>/agencies
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`



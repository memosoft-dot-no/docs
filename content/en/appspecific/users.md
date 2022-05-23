---
title: User and preferences
description: ''
position: 19
category: App specific information
---

## Get authenticated user

```js
URI: https://<im4>/user
```

**Request-type:** `GET`  
**Return data:** `{user}` `(JSON)`

<badge>Since: 0.11 </badge>

Fetch the current authenticated user with info about agency + agencies user has access to.
User preferences included in `user.data`.

## Set user preferences

```js
URI: https://<im4>/user
```

**Request-type:** `POST`  
**Parameters:**
All parameters are optional, and validation is made based on what parameters is specified.

Example:

```json
{app_days_history} (int): Value between 30 and 360
{...}
```

**Return data:** `HTTP 200` on success

<badge>Since: 0.12 </badge>

Set app preferences on user.

## Send reset password link

```js
URI: https://<im4>/forgot
```

**Request-type:** `POST`  
**Parameters:** `{email}` `(string)`: email address  
**Return data:** `HTTP 200` on success

<badge>Since: 0.12</badge>

Sends a reset password link to specified email address

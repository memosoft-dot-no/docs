---
title: Introduction
description: ''
position: 1
category: 'General'
badge: 'Version: 0.23'
---

<img src="/preview.png" class="light-img" width="1280" height="640" alt=""/>
<img src="/preview-dark.png" class="dark-img" width="1280" height="640" alt=""/>

This document describes the **im4** and **memographics** `API` for external systems.

<p class="flex items-center">Enjoy light and dark mode:&nbsp;<app-color-switcher class="inline-flex ml-2"></app-color-switcher></p>

<alert type="warning">
Note: This document is under development, and changes will occur!
</alert>

API notation and code examples will be shown as follows:

- **Client-URI:** `https://<im4>/api/<api-uri>` (valid for Client auth)
- **Request-type:** `<HTTP request type>`
- **Parameters:** `parameter1 (data type): value or description ...`
- **Return data:** `return data (data type): value or description`

<badge>Since: Implemented since this API version</badge>

Description of the function with parameters etc given underneath the API declaration.

## Agency setup

Every agency that is configured in the application, can set up their own list of authenticated external systems. These external systems are technically connected to a separate user account in inmemory or memographics. This separate user belongs to an agency, and the agency administrator has to enable the external `API` functionality in order to set up the external systems. These external systems will be assigned a client id and a client secret which needs to be used while accessing the `API`.

The list of authenticated external systems is available in the agency administration part of **inmemory** or **memographics**.

## User login

Every available user with the proper access configured in agencies can use the `APP API`. Login is username/password-based with subsequent exchange of access tokens.

## Data format

In general, this `API` is based on `HTTP POST` requests where input is given as `JSON` formatted data, or `HTTP GET` requests where parameters are part of the `URI (“REST”-style)`. There may be exceptions to this, which will be fully documented in each API call. Return data is always `JSON` formatted.

## Authentication

In order to be authenticated with **im4**, the external system needs to receive an authentication token. Authentication tokens are long-lived, and never expire. They can however be revoked at any time by the issuing agency. To receive a token, the external system needs to make an API call:

**API: request authentication token**

```js
URI: https://<im4>/oauth/token
Request-type: post
HTTP Headers: None
Parameters:
    grant_type (string): ‘client_credentials’
    client_id (integer): <given client id>
    client_secret (string): <given client secret>
    scope: ‘*’
    All parameters must be sent as form-data.
Return data (JSON):
    token_type (string): ‘Bearer’
    expires_in (int): Number of seconds until expiration
    access_token (string): Generated access token

The returned access_token needs to be provided in any subsequent API calls.
```

<badge>Since: 0.1</badge>

In addition, an external system can authenticate using a valid username/password combination. Any valid user in the system can access the API in this way. Authentication tokens provided in this way are short-lived, however. Here is the API call for this type of authentication:

**API: request username based authentication token (app)**

```js
URI: https://<im4>/api/app/login
Request-type: post
HTTP Headers:
    Accept: application/json
Parameters:
    email (string): <username/email address>
    password (string): <password>
    remember_me (boolean, optional): <0/1>
Return data (JSON):
    token_type (string): ‘Bearer’
    expires_at (datetime): Time of expiration
    access_token (string): Generated access token
The returned access_token needs to be provided in any subsequent API calls.
```

<badge>Since: 0.4</badge>

If the optional parameter remember_me is set to true, the provided token will be valid for one week. Otherwise the token is only valid for 24 hours.
In general, for every subsequent API call, the access_token needs to be specified as part of the HTTP headers:

**API: general HTTP headers**

```js
URI: https://<im4>/<api-call>
Request-type: POST or GET
HTTP Headers:
    Accept: application/json
    Authorization: Bearer <access_token>
```

The `<im4>`-part of the URI is comprised of the server address to the **im4** instance, plus additional paths for the API call. Note that the path is different for Client Authentication and APP authentication:

|         |                                               |
| :------ | :-------------------------------------------- |
| Client: | `https://<server address>/api/<api-call>`     |
| APP:    | `https://<server address>/api/app/<api-call>` |

Please use the proper `<im4>` variant accordingly in the rest of this specification.
Also, the server returns HTTP status codes according to the result of the request:

**API: HTTP status codes**
| | |
| :------ | :-------------------------------------------- |
| `200` | OK - general response whenever the request is successful |
| `400` | Bad Request - The API could not understand the request, possibly due to malformed syntax. |
| `401` | Unathorized - The server could not authorize the request. Invalid credentials given, invalid authorization headers sent, or no access to requested data.
| `403` | Forbidden - The server refuses to fulfill the request - authorization will not help. |
| `404` | Not Found - Could not find anything mathing the request URI. |
| `405` | Method Not Allowed - Given HTTP request method is not allow (f.x. using `GET` where `POST` is required). |
| `419` | Unknown Status - The request resulted in an unknown server status. |
| `500` | Internal Server Error - The server encountered an unexpected condition which prevented it from fulfilling the request. |
| `501` | Not Implemented - The server lacks the ability to fulfill the request. |
| `503` | Service Unavailable - The server is currently unavailable due to temporary overloading or server maintenance. |

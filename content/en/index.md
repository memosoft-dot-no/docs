---
title: Introduction
description: ''
position: 10
category: 'General'
badge: 'Version: 0.25'
---

<img src="/preview.png" class="light-img" width="1280" height="640" alt=""/>
<img src="/preview-dark.png" class="dark-img" width="1280" height="640" alt=""/>

This document describes the **inmemory4** and **memographics** (from this point called the **app**) `API` for external systems.

<p class="flex items-center">Enjoy in light or dark mode:&nbsp;<app-color-switcher class="inline-flex ml-2"></app-color-switcher></p>

API notation and code examples will be shown as follows:

Short description <badge>Since: Implemented since this API version</badge>

- **Client-URI:** `https://<im4>/api/<api-uri>` (valid for Client auth)
- **Request-type:** `<HTTP request type>`
- **Parameters:** <br>
  `{parameter1}` (data type): value or description<br>
  `{parameter2}` (data type): value or description<br>
  ...
- **Return data:** <br> `(data type): value or description`

Additional information

## Agency setup

Every agency configured in the **app** can set up their own list of authenticated external systems. These external systems are technically connected to a separate user account in the **app**. This separate user belongs to an agency and the agency administrator has to enable the external `API` functionality in order to configure the external systems. These external systems will be assigned a `Client id` and a `Client key` which needs to be used while accessing the `API`.

The list of authenticated external systems is available in the agency administration part of **app**.

## Data format

In general, this `API` is based on `HTTP POST` requests where input is given as `JSON` formatted data, or `HTTP GET` and `HTTP DELETE` requests where parameters are part of the `URI (“REST”-style)`. There may be exceptions to this which will be fully documented in each API call. 

## API usage

### Request authentication token
In order to be authenticated with the **app**, external systems needs to receive an authentication token. Authentication tokens are long-lived and never expire. They can however be revoked at any time by the issuing agency. To receive a token, the external system needs to make an API call:

```js
URI: https://<im4>/oauth/token
```

- **Request-type:** `POST` <br>
- **HTTP Headers:** _none_ <br>
- **Parameters:** <br>
  `{grant_type}` (string): ‘client_credentials‘ <br>
  `{client_id}` (integer): `<given client id>` <br> 
  `{client_secret}` (string): `<given client key>`<br>
  `{scope}` (string): ‘\*‘
<alert> Note: All parameters must be sent as form-data. </alert>

- **Return data** (JSON): <br>
  `{token_type}` (string): ‘Bearer’<br>
  `{expires_in}` (int): Number of seconds until expiration<br>
  `{access_token}` (string): Generated access token

The returned `access_token` needs to be provided in any subsequent API calls.

### General HTTP headers

For every subsequent API call after authentication, the `access_token` needs to be specified as part of the HTTP headers:

```js
URI: https://<im4>/<api-call>
```

- **Request-type:** `POST`, `GET` or `DELETE`
- **HTTP Headers:** <br>
  Accept: application/json<br>
  Authorization: Bearer `<access_token>`
  
The `<im4>`-part of the URI is comprised of the server address to the **app** instance, plus additional paths for the API call:

`https://<server address>/api/<api-call>`

Please use the proper `<im4>` variant accordingly in the rest of this specification.
Also, the server returns HTTP status codes according to the result of the request.

### HTTP status codes
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

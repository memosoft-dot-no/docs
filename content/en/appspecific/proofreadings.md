---
title: Proofreadings
description: ''
position: 25
category: App specific information
---

## Get proofreaders in project

```js
URI: https://<im4>/project/{projectId}/proofreaders
```

- **Request-type:** `GET`
- **Return data:** `{mixed}` `(JSON)`

Get proofreaders in project. Name, email and a list of products they are registered as recipients of.  
<badge>Since: 0.22</badge>

## Create proofreading with message – and return proofreading object

```js
URI: https://<im4>/project/{projectId}/proofreadings/create
```

- **Request-type:** `GET`
- **Parameters:**
  - `{doc_id}` – Document id – required if not presentation_id
  - `{presentation_id}` – Presentation_id – required if not doc_id
  - `{user_id}` – Contact person for proofreading
  - `{message?}` – First message in proofreading
  - `{recipients?}` – Optional array of recipients with id?, name? and email)
- **Return data:** `{mixed}` `(JSON)`

Create a new proofreading for specified doc or presentation and return proofreading object – including link to proofreading. Message wil be added as first comment in proofreading.

If recipients sent – these will be added as project recipients. If an existing recipient is used – please include id and recipient will be updated instead of added as a new recipient.  
<badge>Since: 0.22</badge>

## Get proofreading conversation for a specific proofreading

```js
URI: https://<im4>/proofreading/{proofreadingId}
```

- **Request-type:** `GET`
- **Return data:** `{mixed}` `(JSON)`

Get proofreading conversation for a specific proofreading  
<badge>Since: 0.18</badge>

## Comment on a specific proofreading

```js
URI: https://<im4>/proofreading/{proofreadingId}
```

- **Request-type:** `POST`
- **Parameters:** `{message}`
- **Return data:** HTTP 200 on success

Add a comment to a proofreading. Comments will trigger a notification to the recipients. (atm. an email notification)  
<badge>Since: 0.18</badge>

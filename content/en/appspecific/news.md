---
title: News
description: ''
position: 23
category: App specific information
---

## Get list of news available for user

```js
URI: https://<im4>/news
```

- **Request-type:** `GET`
- **Parameters:** `num` (int): Optional to reduce number of news
- **Return data:** `{mixed}` `(JSON)`

Fetch list of published articles available for current authenticated user – including read status. Includes both articles, sticky notes and popups of all type of severity  
<badge>Since 0.12</badge>

## Get news article

```js
URI: https://<im4>/news/{articleId}
```

- **Request-type:** `GET`
- **Return data:** `{mixed}` `(JSON)`

Fetch a single article with all content
<badge>Since 0.17</badge>

## Mark news as read for user

```js
URI: https://<im4>/news/{artcleId}/mark-as-read
```

- **Request-type:** `POST`
- **Parameters:** `{articleId}` - (part of URI) `ID` of article
- **Return data:** HTTP 200 on success

Mark news as read for user – should be set for all types (articles, sticky notes and popups)  
<badge>Since 0.12</badge>

## Mark all unread news as read

```js
URI: https://<im4>/news/mark-all-read
```

- **Request-type:** `POST`
- **Return data:** HTTP 200 on success

Mark news as read for user – should be set for all types (articles, sticky notes and popups)  
<badge>Since 0.17</badge>

## Mark all unread news as read

```js
URI: https://<im4>/news-alert
```

- **Request-type:** `GET`
- **Return data:** HTTP 200 on success

Return number of unread articles + sticky/popup messages  
<badge>Since 0.17</badge>

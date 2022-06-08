---
title: System information
description: 'Fetch available system information'
position: 46
category: Fetching data
---

### Fetch available venues

```js
URI: https://<im4>/venues
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

Fetches list of all available venues.  
<badge>Since 0.11</badge>

### Fetch available funeral types

```js
URI: https://<im4>/funeraltypes
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

Fetches list of all available funeral types.  
<badge>Since 0.4</badge>

### Fetch available ceremony types

```js
URI: https://<im4>/ceremonytypes
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

Fetches list of all available ceremony types.  
<badge>Since 0.4</badge>

### Fetch available autocomplete list for agency

```js
URI: https://<im4>/autocomplete/
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

Fetches all autocomplete lists available through api and available for agency
<alert>Agency specific - if cached locally – cache for each agency</alert>
<alert>Music-archive has author-information in connection to text. All authors is also available in authors-archive</alert>
<badge>Since 0.24</badge>

### Fetch available song archives

```js
URI: https://<im4>/song_archives
    ?includeSongs=true|false
    ?includeTexts=true|false
```

- **Request-type:** `GET`
- **Parameters:**
  - `{includeSongs}` – If true – include songs in archive
  - `{includeTexts}` – If true – and include songs – include texts on songs as well
- **Return data** `{mixed}` `(JSON)`

Fetches available song archives - either only archive info, archive info with songs or archive info with songs and text.  
<badge>Since 0.24</badge>

### API version

```js
URI: https://<im4>/version
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

Fetches current API version.  
<badge>Since 0.4</badge>

---
title: System information
description: ''
position: 46
category: Fetching data
---

### Fetch available venues

Fetch list of all available venues.  <badge>Since 0.11</badge>

```js
URI: https://<im4>/venues
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`


### Fetch available funeral types

Fetch list of all available funeral types. <badge>Since 0.4</badge>

```js
URI: https://<im4>/funeraltypes
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

### Fetch available ceremony types

Fetch list of all available ceremony types. <badge>Since 0.4</badge>

```js
URI: https://<im4>/ceremonytypes
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

### Fetch available autocomplete list for agency

Fetch all autocomplete lists available through api and available for agency <badge>Since 0.24</badge>

```js
URI: https://<im4>/autocomplete/
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

<alert>Agency specific - if cached locally – cache for each agency</alert>
<alert>Music-archive has author-information in connection to text. All authors is also available in authors-archive</alert>

### Fetch available song archives

Fetch available song archives - either only archive info, archive info with songs or archive info with songs and text. <badge>Since 0.24</badge>

```js
URI: https://<im4>/song_archives
?includeSongs=true|false
?includeTexts=true|false
```

- **Request-type:** `GET`
- **Parameters:**
  - `{includeSongs}` (boolean): If true – include songs in archive
  - `{includeTexts}` (boolean): If true – and include songs – include texts on songs as well
- **Return data** `{mixed}` `(JSON)`

### API version

Fetch current API version. <badge>Since 0.4</badge>

```js
URI: https://<im4>/version
```

- **Request-type:** `GET`
- **Parameters:** _none_
- **Return data** `{mixed}` `(JSON)`

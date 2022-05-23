---
title: Project information
description: ''
position: 7
category: Fetching data from iM4
---

External systems can fetch project data for the agency, either the entire data set, a specific key, or a set of comma separated keys (see helper function above for list of valid keys):

### API: fetch available projects

```js
URI: https://<im4>/projects/{agency_id?}
?days={days?}
?search={search?}
?take={take?}&skip={skip?}

Request-type: GET
Parameters:
    {days} – Defaults to 120 days if not specified – skipped if search/take set {search} – Multi-word search – if specified days is ignored.
    {take} – Limit result – used for paging – if specified days is ignored
    {skip} – Skip first x results – used for paging – will only work if skip specified
    {agency_id}
Return data:
    {mixed} (JSON)
```

Fetches list of projects – if user has access to multiple agencies – projects in all agencies will be returned unless `agency_id` is specified <badge>Since 0.1</badge> <br>
Search, take and skip <badge>Since 0.19</badge> <br>

### API: fetch project information

```js
URI: https://<im4>/project/{projectId}

Request-type: GET
Parameters:
    {projectId} - (part of URI) ID of the project
Return data:
    {project} (JSON)
```

Fetches all project info (as defined in valid project keys) as `JSON` data. <badge>Since 0.1</badge>

### API: fetch specific project information

```js
URI: https://<im4>/project/{projectId}/{key|keys}

Request-type: GET
Parameters:
    {projectId} - (part of URI) ID of the project
    {key} - (part of URI) valid project key to be fetched
    {keys} – (part of URI – since v0.8) valid comma separated project keys to be fetched
Return data:
    {mixed} (JSON)
```

Fetches specific project info as `JSON` data. <badge>Since 0.2</badge>

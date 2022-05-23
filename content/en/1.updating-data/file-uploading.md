---
title: File uploading
description: ''
position: 6
category: 'Updating data'
---

The API supports uploading one or more files with the same request. The files can be uploaded to a given category, or as an uncategorized file. There exists a helper function to receive all the categories for a given project:

## Helper functions

### Get project file categories

```js
URI: https://<im4>/project/{projectId}/files/categories
```

Request-type: `GET`
**Parameters:**

- `{projectId}` - (part of URI) ID of the project

**Return data:**

- `{categories}` `(JSON)`

Fetches an array of valid project file categories. <badge>Since 0.3</badge>

Also, there is a function for receiving a list of files in a given category

### Get files in project file category

```js
URI: https://<im4>/project/{projectId}/files/category/{categoryId}
?include_details={true?}&include_size={true?}&include_filter={true?}
```

Request-type: `GET`

**Parameters:**

- `{projectId}` - (part of URI) ID of the project
- `{categoryId}` - (part of URI) ID of category
- `{include_details}` – includes more metadata + preview url
- `{include_size}` – includes width and height of image
- `{include_filter}` – includes used filter if any and if file can have filter applied

**Return data:**

- `{files}` `(JSON)`

Fetches an array of files in given project file category. <badge>Since: 0.4</badge> <br>
`include_details` <badge>Since: 0.20</badge>

Or, if you want all files from all categories:

### Get all project files

```js
URI: https://<im4>/project/{projectId}/files/all
?include_details={true?}
```

Request-type: `GET`
**Parameters:**

- `{projectId}` - (part of URI) ID of the project
- `{include_details}` – gives more metadata + preview url

**Return data:**

- `{files}` `(JSON)`

Fetches an array of files in given project file category. <badge>Since: 0.20</badge>

If a file has property `queued` set, the file is currently processed by a background process. The property `queue` will then tell what kind of process file is process by. <br>
Queue = `upload` is an initial processing of image at upload.<br>
Queue = `pfc` is image improvement or color filtering queue.

`queue` and `queued` are included both with or without the `?include_details` property set.

## Download

There is also a function for downloading the actual files in a given category. If there is only one file, it will be downloaded directly, otherwise a zip-file will be generated:

### Download files in project file category

```js
URI: https://<im4>/project/{projectId}/files/category/{categoryId}/download
```

Request-type: `GET`

**Parameters:**

- `{projectId}` - (part of URI) ID of the project
- `{categoryId}` - (part of URI) ID of category

**Return data:**

- `{files}` downloaded resource file(s)

Fetches actual files in given project file category. <badge>Since: 0.4</badge>

### Download all project files

```js
URI: https://<im4>/project/{projectId}/files/all/download
```

Request-type: `GET`

**Parameters:**

- `{projectId}` - (part of URI) ID of the project
- `{categoryId}` - (part of URI) ID of category

**Return data:**

- `{files}` downloaded resource file(s)

Fetches actual files in given project file category. <badge>Since: 0.4</badge>

## Upload

The function for uploading files to a project, accepts an array of files given as multipart/form-data:

### Upload file to a project file category

```js
URI: https://<im4>/project/{projectId}/files/category/{categoryId}
```

Request-type: `POST`

**Parameters:**

- `{projectId}`: (part of URI) ID of the project
- `{categoryId}`: (part of URI) ID of category - provide 0 to set file as uncategorized
- `{files}`: array of files as multipart/form-data

**Return data:**

- `file_ids}`: Array of file ids

Uploads files to given project and category. <badge>Since: 0.3</badge>  
If uncategorized file, use `categoryId` `0`.

## Sort files

```js
URI: https://<im4>/project/{projectId}/files/sortorder/{file_ids}
```

Request-type: `POST`

**Parameters:**

- `{projectId}`: (part of URI) ID of the project
- `{file_ids}`: (part of URI) File ids in wanted order

**Return data:**

- `{mixed}` `(JSON)`: `file_id` and new sortcode

<badge>Since: 0.12</badge>

## Set metadata and category

```js
URI: https://<im4>/project/{projectId}/files/{file_ids}/set-metadata
```

Request-type: `POST`

**Parameters:**

- `{projectId}`: (part of URI) ID of the project
- `{file_ids}`: (part of URI) File ids
- `{caption}`: picture caption
- `{byline}`: second picture caption – used for flower greetings
- `{priority}`: setting priority for image (0,1,2)
- `{category_id}`: setting image category

<badge>Since: 0.20</badge>

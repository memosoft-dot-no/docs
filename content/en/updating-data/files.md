---
title: Files
description: ''
position: 22
category: 'Updating data'
---

The API supports uploading one or more files with the same request. The files can be uploaded to a given category, or as an uncategorized file. There exists a helper function to receive all the categories for a given project

## Get file and category info

### Get project file categories

Fetch an array of valid project file categories. <badge>Since 0.3</badge>

```js
URI: https://<im4>/project/{projectId}/files/categories
```

- **Request-type:** `GET`
- **Parameters:**
  `{projectId}` (part of URI): ID of the project
- **Return data:** `{categories}` `(JSON)`

### Get files in project file category

Fetch an array of files in given project file category. <badge>Since: 0.4</badge> <br>

```js
URI: https://<im4>/project/{projectId}/files/category/{categoryId}
?include_details={true?}
&include_size={true?}
&include_filter={true?}
```

- **Request-type:** `GET`
- **Parameters:** <br>
  `{projectId}` (part of URI): ID of the project <br>
  `{categoryId}` (part of URI): ID of category <br>
  `{include_details}`(boolean): includes more metadata + preview url <badge>Since: 0.20</badge> <br>
  `{include_size}` (boolean): includes width and height of image <br>
  `{include_filter}` (boolean): includes used filter if any and if file can have filter applied
- **Return data:** `{files}` `(JSON)`

### Get all project files

Fetch an array of files in given project file category. <badge>Since: 0.20</badge>

```js
URI: https://<im4>/project/{projectId}/files/all
?include_details={true?}
```

- **Request-type:** `GET`
- **Parameters:**
  - `{projectId}` (part of URI): ID of the project
  - `{include_details}` (boolean): gives more metadata + preview url
- **Return data:** `{files}` `(JSON)`

If a file has property `queued` set, the file is currently processed by a background process. The property `queue` will then tell what kind of process file is process by. <br>
Queue = `upload` is an initial processing of images at upload.<br>
Queue = `pfc` is image improvement or color filtering queue.

`queue` and `queued` are included both with or without the `?include_details` property set.

## Download

### Download files in project file category

Fetch all files in given project file category. <badge>Since: 0.4</badge>

```js
URI: https://<im4>/project/{projectId}/files/category/{categoryId}/download
```

- **Request-type:** `GET`
- **Parameters:** <br>
  `{projectId}` (part of URI): ID of the project <br>
  `{categoryId}` (part of URI): ID of category
- **Return data:**
  `{files}` downloaded resource file(s)

If there is only one file, it will be downloaded directly, otherwise a zip-file will be generated:

### Download all project files

Fetch all files in project. <badge>Since: 0.4</badge>

```js
URI: https://<im4>/project/{projectId}/files/all/download
```

- **Request-type:** `GET`
- **Parameters:**
  - `{projectId}` (part of URI): ID of the project
- **Return data:**
  `{files}` downloaded resource file(s)

## Upload

The function for uploading files to a project accepts an array of files given as multipart/form-data:

### Upload file to a project file category

Uploads files to given project and category. <badge>Since: 0.3</badge>

```js
URI: https://<im4>/project/{projectId}/files/category/{categoryId}
```

- **Request-type:** `POST`
- **Parameters:**
  - `{projectId}` (part of URI): ID of the project
  - `{categoryId}` (part of URI): ID of category - provide 0 to set file as uncategorized
  - `{files}`: array of files as multipart/form-data
- **Return data:**
  `file_ids}`: Array of file ids

If uncategorized file, use `categoryId` `0`.

## Sort files

Sort files in project by specifying file ids in correct order. <badge>Since: 0.12</badge>

```js
URI: https://<im4>/project/{projectId}/files/sortorder/{file_ids}
```

- **Request-type:** `POST`
- **Parameters:**
  - `{projectId}` (part of URI): ID of the project
  - `{file_ids}` (part of URI): File ids in wanted order
- **Return data:**
  `{mixed}` `(JSON)`: `file_id` and new sortcode

## Set metadata and category

Set metadata and category on files <badge>Since: 0.20</badge>

```js
URI: https://<im4>/project/{projectId}/files/{file_ids}/set-metadata
```

- **Request-type:** `POST`
- **Parameters:**
  - `{projectId}` (part of URI): ID of the project
  - `{file_ids}` (part of URI): File ids
  - `{caption}` (string): picture caption
  - `{byline}` (string): second picture caption – used for flower greetings
  - `{priority}` (integer): setting priority for image (0,1,2)
  - `{category_id}` (integer): setting image category

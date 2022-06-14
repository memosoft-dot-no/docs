---
title: Program items
description: ''
position: 42
category: Fetching data
---

External clients can fetch and handle project programitems, download program schedule, get list of available program templates and import these to project.<br>

### Load program items

Fetch all project program items.<br>
Loading program items is done through project keys as described [here](project-information#fetch-specific-project-information)

```js
URI: https://<im4>/projects/{projectId}/programitems
```

- **Request-type:** `GET`
- **Return data:**
  `{mixed}` `(JSON)`

### Update program items
Updating program items id done through project keys as described [here](update-project)

```js
URI: https://<im4>/project/{projectId}/programitems
```

- **Request-type:** `GET`
- **Parameters:** `{projectId}` (part of URI): `ID` of the project
- **Return data:** ` {project}` `(JSON)`

### Download program schedule

Download program schedule as PDF <badge>Since 0.25</badge><br>
Notes not shown in program sheets is also included in schedule and by specifying type=full song verses will also be included 

```js
URI: https://<im4>/project/{projectId}/programitems/download-schedule
?type={full?}
```

- **Request-type:** `GET`
- **Parameters:**<br>
  `{projectId}` (part of URI): `ID` of the project<br>
  `{type}` (string): Type of schedule. If set to `full` song verses will be included
- **Return data:**
  `{file}` downloaded pdf file

### Load program templates

Load a list of available program templates for project <badge>Since 0.25</badge><br>
A program template is a set of default program items used globally, by agency or by venue.<br>
A program template can be imported to a project to make further manual setup easier

```js
URI: https://<im4>/project/{projectId}/program_templates
```

- **Request-type:** `GET`
- **Parameters:** `{projectId}` (part of URI): `ID` of the project
- **Return data:** `{mixed}` `(JSON)` JSON list with template id, scope, name and number of program items

### Import program template

Import a program template to project <badge>Since 0.25</badge><br>
This will replace all existing program items with program items from program template

```js
URI: https://<im4>/project/{projectId}/programitems/import/{sourcetemplate}
```

- **Request-type:** `GET`
- **Parameters:**<br>
  `{projectId}` (part of URI): `ID` of the project<br>
  `{sourcetemplate}` (part of URI): Program template id
- **Return data:** HTTP 200 on success

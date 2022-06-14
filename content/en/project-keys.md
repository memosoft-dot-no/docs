---
title: Project keys
description: ''
position: 11
category: General
---

`Projects` is the main part of the **app**. This chapter provides a complete list of all available project keys. This list can also be retrieved programmatically by using the [get valid project keys](#fetch-available-project-keys) helper function.

## Valid project keys
### Project details
| Key                       | R/W | Type       | Comment                                                                                                                                                                                                                           |
| :------------------------ | :-- | :--------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `details`                 | R   | -          | Shortcut to get most used project keys.<br> Can be combined with other keys in same request. <br>(keys with (*) in comment is included in details)                                                                                |
| `agency_id  `             | R   | Int        | ID of owner agency (*)                                                                                                                                                                                                            |
| `ordernumber`             | RW  | String     | Order number for project (*)                                                                                                                                                                                                      |
| `subject_firstname`       | RW  | String     | First name (*)                                                                                                                                                                                                                    |
| `subject_lastname`        | RW  | String     | Last name (*)                                                                                                                                                                                                                     |
| `subject_dob`             | RW  | Date       | Date of birth (YYYY-MM-DD) (*)                                                                                                                                                                                                    |
| `subject_dob_formatted`   | R   | String     | Date of birth formatted                                                                                                                                                                                                           |
| `subject_dod`             | RW  | Date       | Date of death (YYYY-MM-DD) (*)                                                                                                                                                                                                    |
| `subject_dod_formatted`   | R   | String     | Date of death formatted                                                                                                                                                                                                           |
| `ceremony_date`           | RW  | Date       | Date of ceremony (YYYY-MM-DD) (*)                                                                                                                                                                                                 |
| `ceremony_time`           | RW  | Time       | Time of ceremony (HH:MM) (*)                                                                                                                                                                                                      |
| `ceremony_date_formatted` | R   | String     | Date of ceremony formatted                                                                                                                                                                                                        |
| `ceremony_type`           | R   | Array      | Type of ceremony                                                                                                                                                                                                                  |
| `ceremony_type`           | W   | int        | ID of ceremony type                                                                                                                                                                                                               |
| `funeral_type`            | R   | Array      | Type of funeral                                                                                                                                                                                                                   |
| `funeral_type`            | W   | Int        | ID of funeral type                                                                                                                                                                                                                |
| `contact_person`          | R   | Array      | Assigned contact person. (*) See table `contact_person` for more details.                                                                                                                                                         |
| `contact_person`          | W   | String/Int | Email or ID of contact person (agency-user)                                                                                                                                                                                       |
| `venue`                   | R   | Array      | Assigned venue. See table venue for mor details                                                                                                                                                                                   |
| `venue`                   | W   | Int        | ID of venue                                                                                                                                                                                                                       |
| `venue_name`              | RW  | String     | Name of the venue. (*)                                                                                                                                                                                                            |
| `participants`            | RW  | Array      | List of participants (where role is set) (*). See table participants for more details. Write: Overwrite if matching role, otherwise only adding new. No existing are removed                                                      |
| `programitems`            | RW  | Array      | List of program items for the ceremony. See table programitems for more details.                                                                                                                                                  |
| `texts`                   | RW  | Array      | List of texts used in the project. See table texts for more details.                                                                                                                                                              |
| `greetings`               | RW  | Array      | List of greetings. See table greetings for more details.                                                                                                                                                                          |
| `proofreaders`            | RW  | Array      | List of proofreaders See table proofreaders for more details. Updating if match on email (or name if email is empty), else creating new proofreader. No existing proofreaders are removed                                         |
| `delivery`                | R   | Array      | List of delivery addresses.                                                                                                                                                                                                       |
| `link`                    | RW  | String     | URI to memorial page                                                                                                                                                                                                              |
| `designs`                 | RW  | Array      | List of preferred designs per product type See table preferred_designs for more details. Write: Adding designs not already set for specific `product_type` Write: Adding designs not already set. No existing designs are removed |
| `orders`                  | R   | Array      | List of orders. See table orders for more details.                                                                                                                                                                                |
| `timecut_id`              | RW  | String     | Id used for Timecut integration (if not ordernumber is correct for integration)                                                                                                                                                   |
| `eulogica_id`             | RW  | String     | Eulogica project id                                                                                                                                                                                                               |
| `bitnet_id`               | RW  | String     | Bitnet project id                                                                                                                                                                                                                 |
| `adstate_id`              | RW  | String     | Id used for Adstate integration (if not ordernumber is correct for integration)                                                                                                                                                   |
| `registration_link`       | R   | String     | Short link to digital registration                                                                                                                                                                                                |
| `booklet_link`            | R   | String     | Short link to booklet poster                                                                                                                                                                                                      |

### Additional project related details

Some custom details not included when requesting full project information

| Key                       | R/W | Type       | Comment                                                                                                                                                                                                                           |
| :------------------------ | :-- | :--------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `contact_persons`         | R   | Array      | List of contact persons available for this project (agency users or users in agencies with shared access to agency projects)                                                                                                      |
| `proofreading_batches`    | R   | Array      | List of proofreading batches. See table proofreading batches for more details                                                                                                                                                     |
| `order/{id}`              | R   | Array      | Fetch all info for one order.                                                                                                                                                                                                     |

### Table: `contact_person`

| Key         | R/W | Type   | Comment       |
| :---------- | :-- | :----- | :------------ |
| `id`        | R   | Int    | ID            |
| `agency_id` | RW  | Int    | Agency ID     |
| `firstname` | RW  | String | First name    |
| `lastname`  | RW  | String | Last name     |
| `email`     | RW  | String | Email address |
| `phone`     | RW  | String | Phone number  |
| `name`      | R   | String | Full name     |

### Table: `participants`

| Key           | R/W | Type   | Comment                 |
| :------------ | :-- | :----- | :---------------------- |
| `id`          | R   | Int    | ID                      |
| `projectc_id` | R   | Int    | Project ID              |
| `role`        | RW  | String | Role of the participant |
| `name`        | RW  | String | Name of the participant |
| `sortcode`    | RW  | Int    | Sortcode                |

### Table: `programitems`

| Key          | R/W | Type   | Comment                                                                                   |
| :----------- | :-- | :----- | :---------------------------------------------------------------------------------------- |
| `id`         | R   | Int    | ID                                                                                        |
| `type`       | RW  | String | Type of item, values: `[‘programpost’, ‘song’, ‘editortext’, ‘participants’, ‘lastpage’]` |
| `sortcode`   | RW  | Int    | Sortcode                                                                                  |
| `data`       | RW  | Array  | Varies from type of item. See subtables below.                                            |
| `created_at` | R   | DT     | Created at timestamp                                                                      |
| `updated_at` | R   | DT     | Updated at timestamp                                                                      |

### Program item subtable: `programpost`

| Key                 | R/W | Type   | Comment               |
| :------------------ | :-- | :----- | :-------------------- |
| `programpost_macro` | R   | String | Not used              |
| `title`             | RW  | String | Title                 |
| `byline`            | RW  | String | Performed by / byline |
| `song`              | RW  | String | Song name             |
| `author`            | RW  | String | Authored/composed by  |

### Program item subtable: `song`

| Key                  | R/W | Type   | Comment                                                                                                                             |
| :------------------- | :-- | :----- | :---------------------------------------------------------------------------------------------------------------------------------- |
| `song_id`            | RW  | Int    | ID of the song                                                                                                                      |
| `song_verse_numbers` | RW  | Int    | Flag whether to prefix verse with verse number                                                                                      |
| `title`              | RW  | String | Title of song / song-number                                                                                                         |
| `text`               | RW  | String | Text of song                                                                                                                        |
| `byline`             | RW  | String | Author/composer/byline                                                                                                              |
| `verses`             | RW  | Array  | List of verse numbers <br> Write: Could also be a comma separated string of verses, or a span. E.g: “1,3-4,5” gives vers 1,3,4 and 5 |
| `song_number`        | R   | Int    | Not used                                                                                                                            |
| `archive_title`      | R   | String | Not used                                                                                                                            |

### Program item subtable: `editortext`

| Key            | R/W | Type   | Comment  |
| :------------- | :-- | :----- | :------- |
| `title`        | RW  | String | Title    |
| `text`         | RW  | String | Text     |
| `byline`       | RW  | String | Byline   |

### Program item subtable: `participants`

| Key                  | R/W | Type   | Comment  |
| :------------------- | :-- | :----- | :------- |
| `participants_macro` | R   | String | Not used |

### Table: `greetings`

| Key                | R/W | Type   | Comment         |
| :----------------- | :-- | :----- | :-------------- |
| `id`               | R   | Int    | Greetings ID    |
| `project_id`       | R   | Int    | Project ID      |
| `author`           | RW  | String | Greeting author |
| `text`             | RW  | String | Greeting text   |
| `has_big_greeting` | RW  | Bool   | “big” greeting  |
| `sortcode`         | RW  | Int    | Sortcode        |

### Table: `preferred designs`

| Key                 | R/W | Type   | Comment                                                                     |
| :------------------ | :-- | :----- | :-------------------------------------------------------------------------- |
| `id`                | RW  | Int    | Design ID                                                                   |
| `name`              | R   | String | Not used                                                                    |
| `cover_preview_url` | R   | String | Not used                                                                    |
| `feed_preview_url`  | R   | String | Not used                                                                    |
| `product_type`      | RW  | String | ProductType [book, booklet, card, portrait]                                 |
| `legacy_code`       | W   | String | Optional: Design-code from IM3 (used instead of `design_id`)                |
| `design_code`       | W   | String | Optional: Design-code = design_id + 1000. Always 4-digits and what user see |

### Table: `delivery`

| Key       | R/W | Type   | Comment                                                 |
| :-------- | :-- | :----- | :------------------------------------------------------ |
| `id`      | R   | Int    | Delivery ID                                             |
| `name`    | RW  | String | Recipient name                                          |
| `phone`   | RW  | String | Recipient phone number                                  |
| `email`   | RW  | String | Recipient email                                         |
| `comment` | RW  | String | Delivery comment                                        |
| `data`    | RW  | Array  | Product type with number of items (See subtable:`data`) |
| `address` | RW  | Array  | Address (See subtable: `address`)                       |
| `status`  | R   | Array  | Label and Color of status                               |

### Delivery subtable: `data`

| Key           | R/W | Type  | Comment                                                                                                 |
| :------------ | :-- | :---- | :------------------------------------------------------------------------------------------------------ |
| `recipientOf` | RW  | Array | Array of each product_type with a number of items to receive. <br>Example: `{“booklet”:100,”book”:10”}` |

### Delivery subtable: `address`

| Key       | R/W | Type   | Comment        |
| :-------- | :-- | :----- | :------------- |
| `address` | RW  | String | Street address |
| `zip`     | RW  | String | Zip            |
| `city`    | RW  | String | City           |

### Table: `proofreaders`

| Key     | R/W | Type   | Comment                                                    |
| :------ | :-- | :----- | :--------------------------------------------------------- |
| `Id`    | R   | Int    | Proofreader ID                                             |
| `Name`  | RW  | String | Proofreader name                                           |
| `email` | RW  | String | Proofreader email                                          |
| `data`  | RW  | Array  | Product type with number of items<br>(See subtable:`data`) |

### Proofreaders subtable: `data`

| Key           | R/W | Type  | Comment                                                                 |
| :------------ | :-- | :---- | :---------------------------------------------------------------------- |
| `recipientOf` | RW  | Array | Array of each product_type to receive.<br>Example: `[“booklet”,”book”]` |

### Table: `proofreading_batches`

| Key                   | R/W | Type   | Comment                                                |
| :-------------------- | :-- | :----- | :----------------------------------------------------- |
| `id`                  | R   | Int    | Proofreading batch ID                                  |
| `doc_id`              | R   | Int    | Document ID                                            |
| `agency_id`           | R   | Int    | Agency ID                                              |
| `agency_name`         | R   | String | Agency name                                            |
| `doc_name`            | R   | String | Document name                                          |
| `status_code`         | R   | String | Batch status: null = open. Else approved or rejctedted |
| `product_type`        | R   | String | Product type: Example `“booklet”`, `“book”`, `“card”`  |
| `project_id`          | R   | Int    | Project ID                                             |
| `project_name`        | R   | String | Project name                                           |
| `project_ordernumber` | R   | String | Project Order Number                                   |
| `subject_firstname`   | R   | String | Deceased firstname                                     |
| `subject_lastname`    | R   | String | Deceased lastname                                      |
| `contact_firstname`   | R   | String | Contact person firstname                               |
| `contact_lastname`    | R   | String | Contact person lastname                                |
| `status`              | R   | Array  | Label and Color                                        |
| `created_at`          | R   | DT     | Batch created datetime                                 |
| `proofreadings`       | R   | Array  | Proofreadings in batch (see subtable `proofreading`)   |

### Proofreading batches subtable: `proofreadings`

| Key                     | R/W | Type   | Comment                       |
| :---------------------- | :-- | :----- | :---------------------------- |
| `id`                    | R   | String | Proofreading ID               |
| `proofreading_batch_id` | R   | Int    | Proofreading Batch ID         |
| `message`               | R   | String | Proofreading message          |
| `user_id`               | R   | Int    | Contact person ID             |
| `link`                  | R   | String | Link to proofreading          |
| `title`                 | R   | String | Proofreading title            |
| `created_at`            | R   | DT     | Sent when datetime            |
| `doc_updated_at`        | R   | DT     | Document last update datetime |
| `Recipients`            | R   | Array  | Name, Email and Opened_at     |

### Table: `orders`

| Key                   | R/W | Type    | Comment                                                                                                                                                                                  |
| :-------------------- | :-- | :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `order_id`            | R   | Int     | Order ID                                                                                                                                                                                 |
| `order_number`        | R   | Int     | Order number                                                                                                                                                                             |
| `project_ordernumber` | R   | String  | Project Order number                                                                                                                                                                     |
| `project_id`          | R   | Int     | Project ID                                                                                                                                                                               |
| `subject_firstname`   | R   | String  | Subject firstname                                                                                                                                                                        |
| `subject_lastname`    | R   | String  | Subject lastname                                                                                                                                                                         |
| `agency_id`           | R   | Int     | Agency ID                                                                                                                                                                                |
| `agency_name`         | R   | String  | Agency name                                                                                                                                                                              |
| `order_date`          | R   | DT      | Ordered when datetime                                                                                                                                                                    |
| `numbers`             | R   | Int     | Number of items in order                                                                                                                                                                 |
| `product`             | R   | String  | Product name                                                                                                                                                                             |
| `price`               | R   | Float   | Order price                                                                                                                                                                              |
| `extra`               | R   | Array   | Extra wares on order. Array with Name and Numbers for each ware.                                                                                                                         |
| `currency`            | R   | String  | Price currency                                                                                                                                                                           |
| `email`               | R   | String  | Email for order                                                                                                                                                                          |
| `status`              | R   | Array   | Label, Color and Date of last status                                                                                                                                                     |
| `state`               | R   | String  | Order states: <br>null = new order <br>in_production = in production + other statuses between until delivered state<br>delivered = complete/sent/invoiced <br>cancel = cancelled/aborted |
| `is_doc`              | R   | Boolean | Order of a printed document                                                                                                                                                              |
| `is_service`          | R   | Boolean | Order of a service                                                                                                                                                                       |

Loading a single order also includes info about recipients, addresses and all order status updates

## Fetch available project keys

The API has a helper function to receive all valid project keys/properties which can be set by an external client.
`ProjectId` has to be specified because some keys can be agency or project specific 

```js
URI: https://<im4>/project/{projectId}/keys
```

- **Request-type:** `GET`
- **Parameters:** `{projectId}` (part of URI): `ID` of the project
- **Return data:**

```json
{[key] => (
    [comment] => Comment on key
    [read] => Readable key
    [write] => Writable key
), ... }
```

<alert> Note: every property comes with a comment and a flag if it is readable and/or writeable.</alert>
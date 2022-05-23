---
title: Code examples
description: ''
position: 30
category: Examples
---

This chapter shows various code examples (in PHP) of how to access the API.

## Access the API with client authentication

```php[php]
$r = $client->post(
    'https://no-stage-inmemory4.gc.no/oauth/token',
    [ 'form_params' => [
        'grant_type' => 'client_credentials',
        'client_id' => CLIENT_ID,
        'client_secret' => CLIENT_SECRET,
        'scope' => '*', ] ] );

$token = json_decode((string) $r->getBody(), true)['access_token'];
```

## Access the API with APP authentication

```php[php]
$r = $client->post(
    'https://no-stage-inmemory4.gc.no/api/app/login', [
        'form_params' => [
            'email' => USER_EMAIL,
            'password' => USER_PASSWORD,
            'remember_me' => 1 ] ] );

$token = json_decode((string) $r->getBody(), true)['access_token'];
```

## Create new project

```php[php]
// Example data
$data = [
    'subject_firstname' => 'API TEST',
    'subject_lastname' => 'LASTNAME',
    'subject_dob' => '1976-05-10',
    'subject_dod' => '2018-10-20',
    'ceremony_date' => '2018-11-01',
    'ceremony_time' => '11:00',
    'venue_name' => 'API VENUE',
    'participants' => [
        ['role' => 'APIother', 'name' => 'API Polly Participant'],
        ['role' => 'APIother2', 'name' => 'API Petra Participant']
    ],
    'programitems' => [
        [
            'type' => 'text',
            'data' => [
                'title' => 'Prayer', 'data' => [],
                'text' => 'Prayer text',
                'byline' => 'Herman Prayer',
            ],
            'sortcode' => 0, 'frame' => 0, 'lastpage' => 0
        ],
        [
            'type' => 'song',
            'data' => [
                'title' => 'Amazing Grace' | songbook-number,
                'byline' => 'John Newton'
                'text' => 'Amazing Grace text',
                'verses' => '1,3-4,5' | [1,3,4,5]
            ],
            'sortcode' => 0,
            'lastpage' => 0
        ],
        [
            'type' => 'programpost',
            'data' => [
                'title' => 'Song'
                'song' => 'You’ll be in my heart',
                'author' => 'Paul Simon', 'performance'
                'byline' => 'Sandra Soloist'],
            ],
                'sortcode' => 0,
                'lastpage' => 0
            ]
    ],
    'texts' => [
        [
        'title' => 'Text title', 'code' => 'UniqueCode', 'author' =>
        'Author', 'content' => 'This is the content'
        ]
    ],
    'projectfields' => [
        ['type' => 'text', 'label' => 'Label', 'content' => 'The content'],
        [
            'type' => 'textarea', 'label' => 'Label2', 'content' =>
            'Another content'
        ],
        [
            'type' => 'date', 'label' => 'Label3', 'content' =>
            '2010-01-01'
        ]
    ],
    'delivery' => [
        [
            'address' => 'Street', 'zip' => '1234', 'city' => 'Mytown',
            'data' => [
                'name' => 'Recipient Name', 'comment' => 'A comment',
                'phone' => '12345678', 'email' => 'email@me.com'
            ]
        ]
    ],
    'comments' => [
        ['title' => 'A comment', 'content' => 'Here’s a comment'],
        ['title' => 'Another', 'content' => 'Another comment']
        ]
    ];

$r = $client->post(
    'https://no-stage-inmemory4.gc.no/api/project', [
        'headers' => [
            'Authorization' => 'Bearer ' . $token,
            'Accept' => 'application/json'
        ],
        'form_params' => [
            'data' => json_encode($data)
        ]
    ]
);

$returnValue = json_decode((string) $r->getBody());
```

## Fetch valid keys/properties

```php[php]
$r = $client->get(
    'https://no-stage-inmemory4.gc.no/api/project/6/keys', [
        'headers' => [
            'Authorization' => 'Bearer ' . $token,
            'Accept' => 'application/json'
        ]
    ]
);

print_r(json_decode((string) $r->getBody());

// Prints:
stdClass Object
(
    [subject_firstname] => stdClass Object
        (
            [comment] => api.subject_firstname
            [read] => 1
            [write] => 1
        )
    [subject_lastname] => stdClass Object
        (
            [comment] => api.subject_lastname
            [read] => 1 [write] => 1
        )
...

```

## Upload file

```php[php]
// File upload
$r = $client->request(
    'POST', 'https://no-stage-inmemory4.gc.no/api/project/6/files/category/2', [
        'headers' => [
            'Authorization' => 'Bearer ' . $token,
            'Accept' => 'application/json'
        ],
        'multipart' => [
            [
                'Content-type' => 'multipart/form-data',
                'name' => 'files[]',
                'contents' => fopen('picture.jpg', 'r')
            ],
            [
            'Content-type' => 'multipart/form-data',
            'name' => 'files[]',
            'contents' => fopen('document.pdf', 'r')
            ]
        ]
    ]
);
```

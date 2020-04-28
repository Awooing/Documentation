---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php

toc_footers:
  - <a href='https://awooing.moe'>2020 &copy; Awooing.moe, Vottus</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome, this is the documentation of the Awooing.moe API, from which you can get information from our website.. 
On the right, you can see examples in Shell, JS and PHP

The main API endpoint is `https://rest.awooing.moe/api/v1`

The CDN endpoint is `https://cdn.awooing.moe`

# Council Members

## Get all council members

```shell
curl "https://rest.awooing.moe/api/v1/council"
```

```php
$options = [
    "http"=>[
        "method"=>"GET"
    ]
];
$context = stream_context_create($options);
$members = file_get_contents("https://rest.awooing.moe/api/v1/council", false, $context);
$json = json_decode($members);

-- OR --

$members = file_get_contents("https://rest.awooing.moe/api/v1/council");
$json = json_decode($members);
// easier method if you don't need to set any additional parameters
```

> The above command/code returns JSON structured like this:

```json
[
    {
        "id": 4,
        "name": "Rin",
        "position": "Head of the council",
        "about": "Some lorem-ipsum nonsense text about Rin here lel.",
        "discord_id": "376121356766674948",
        "user_id": 0
    },
    {
        "id": 5,
        "name": "Tokichii",
        "position": "High wan-wan",
        "about": "Some lorem-ipsum nonsense text about Tokichii here lel.",
        "discord_id": "227266184737849366",
        "user_id": 0
    }
]
```

This endpoint retrieves all council members.

### HTTP Request

`GET https://rest.awooing.moe/api/v1/council`

### Response JSON

Inside of the JSON are arrays with values described below:

Key | Type | Description
--------- | ------- | -----------
id | int | Returns the id of the Council Member
name | string | Name of the Council Member
about | string | About the Council Member
discord_id | string | Discord ID of the Council Member
user_id | string | Website User ID of the Council Member 

<aside class="notice">
ID isn't the same as the user id on the website!
</aside>

<aside class="notice">
If user_id returns 0, it means that they're not registered.
</aside>

## Get a specific council member

```shell
curl "https://example.com/api/council/5"
```

```php
$options = [
    "http"=>[
        "method"=>"GET"
    ]
];
$context = stream_context_create($options);
$members = file_get_contents("https://rest.awooing.moe/api/v1/council/5", false, $context);
$json = json_decode($members);

// --- OR --

$members = file_get_contents("https://rest.awooing.moe/api/v1/council/5");
$json = json_decode($members);
// easier method if you don't need to set any additional parameters

// ... and then
echo $json->username; // prints "Tokichii"
```

> The above command/code returns JSON structured like this:

```json
{
    "id": 5,
    "name": "Tokichii",
    "position": "High wan-wan",
    "about": "Some lorem-ipsum nonsense text about Tokichii here lel.",
    "discord_id": "227266184737849366",
    "user_id": 0
}
```

This endpoint retrieves a specific council member.

### HTTP Request

`GET http://rest.awooing.moe/api/v1/council/<ID>`

### URL Parameters

Parameter | Type | Description
--------- | ----------- | -----------
ID | int | The ID of the council member to retrieve

### JSON Response

Key | Type | Description
--------- | ------- | -----------
id | int | Returns the id of the Council Member
name | string | Name of the Council Member
about | string | About the Council Member
discord_id | string | Discord ID of the Council Member
user_id | string | Website User ID of the Council Member 

<aside class="notice">
ID isn't the same as the user id on the website!
</aside>

<aside class="notice">
If user_id returns 0, it means that they're not registered.
</aside>


# User

## Get information of logged in user

```shell
curl "https://rest.awooing.moe/api/v1/user"
    -H "Cookie: PHPSESSID=<SessionID>;"
```
<aside class="notice">
If you are not logged in (missing session id cookie), it will throw an error 400. 
</aside>

```php
$options = [
    "http"=>[
        "method"=>"GET",
        "header"=>"Cookie: PHPSESSID=<SessionID>;"
    ]
];
$context = stream_context_create($options);
$user = file_get_contents("https://rest.awooing.moe/api/v1/user", false, $context);
$json = json_decode($user);

// ... and then
echo $json->username; // prints username
```

> The above command/code returns JSON structured like this:

```json
{
    "id": 13,
    "username": "user",
    "email": "testing@example.com",
    "showAs": "user",
    "active": true,
    "banned": true,
    "role": "member",
    "discord_id": "unset",
    "location": "unset",
    "join_date": "28/04/2020"
}
```

This endpoint retrieves information about the logged in user.

### HTTP Request

`GET https://rest.awooing.moe/api/v1/user`

### Response JSON 

Key | Type | Description
--------- | ------- | -----------
id | int | Returns the id of the user
username | string | Username of the user
email | string | Email of the user
showAs | string | The public name (in comments, etc..)
active | boolean | Boolean if the user is active - verified email
banned | boolean | Boolean if the user is banned on the website
role | string | Role of the user
discord_id | string | Discord ID of the user
location | string | Location of the user
join_date | string | When the user registered

<aside class="notice">
ID isn't the same as the user id on the website!
</aside>

<aside class="notice">
If user_id returns 0, it means that they're not registered.
</aside>

## Get a specific council member

```shell
curl "https://example.com/api/council/5"
```

```php
$options = [
    "http"=>[
        "method"=>"GET"
    ]
];
$context = stream_context_create($options);
$members = file_get_contents("https://rest.awooing.moe/api/v1/council/5", false, $context);
$json = json_decode($members);

// --- OR --

$members = file_get_contents("https://rest.awooing.moe/api/v1/council/5");
$json = json_decode($members);
// easier method if you don't need to set any additional parameters

// ... and then
echo $json->username; // prints "Tokichii"
```

> The above command/code returns JSON structured like this:

```json
{
    "id": 5,
    "name": "Tokichii",
    "position": "High wan-wan",
    "about": "Some lorem-ipsum nonsense text about Tokichii here lel.",
    "discord_id": "227266184737849366",
    "user_id": 0
}
```

This endpoint retrieves a specific council member.

### HTTP Request

`GET http://rest.awooing.moe/api/v1/council/<ID>`

### URL Parameters

Parameter | Type | Description
--------- | ----------- | -----------
ID | int | The ID of the council member to retrieve

### JSON Response

Key | Type | Description
--------- | ------- | -----------
id | int | Returns the id of the Council Member
name | string | Name of the Council Member
about | string | About the Council Member
discord_id | string | Discord ID of the Council Member
user_id | string | Website User ID of the Council Member 

<aside class="notice">
ID isn't the same as the user id on the website!
</aside>

<aside class="notice">
If user_id returns 0, it means that they're not registered.
</aside>


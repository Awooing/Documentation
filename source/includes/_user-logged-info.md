# User

## Info about logged in user

```shell
curl "https://rest.awooing.moe/api/v1/user"
    --cookie "PHPSESSID=<SessionID>"
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


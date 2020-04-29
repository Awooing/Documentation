## Info about specific user

```shell
curl "https://example.com/api/user/10"
```

<aside class="notice">
If a user is logged in and the ID requested is the same as his,
the result will be same as if you tried to query the logged in user (see "Get information of logged in user"),
thus the private information will be visible.
</aside>

```php
$options = [
    "http"=>[
        "method"=>"GET"
    ]
];
$context = stream_context_create($options);
$members = file_get_contents("https://rest.awooing.moe/api/v1/user/12", false, $context);
$json = json_decode($members);

// --- OR --

$members = file_get_contents("https://rest.awooing.moe/api/v1/user/12");
$json = json_decode($members);
// easier method if you don't need to set any additional parameters

// ... and then
echo $json->username; // prints "AwooRin"
```

> The above command/code returns JSON structured like this:

```json
{
    "id": 12,
    "username": "AwooRin",
    "showAs": "Awoo Councilman Rin",
    "role": "member",
    "discord_id": "376121356766674948",
    "location": "unset",
    "join_date": "19/04/2020"
}
```

This endpoint retrieves a specific council member.

### HTTP Request

`GET http://rest.awooing.moe/api/v1/user/<ID>`

### URL Parameters

Parameter | Type | Description
--------- | ----------- | -----------
ID | int | The ID of the user to retrieve

### JSON Response

Key | Type | Description
--------- | ------- | -----------
id | int | Returns the id of the user
username | string | Username of the user
showAs | string | The public name (in comments, etc..)
role | string | Role of the user
discord_id | string | Discord ID of the user
location | string | Location of the user
join_date | string | When the user registered


<aside class="notice">
If <code>location</code> or <code>discord_id</code> return unset, it means that user not set the value,
in case of <code>discord_id</code> it's that the user didn't link their account with discord.
</aside>

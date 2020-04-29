## Specific council member

```shell
curl "https://rest.awooing.moe/api/v1/council/5"
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

`GET https://rest.awooing.moe/api/v1/council/<ID>`

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

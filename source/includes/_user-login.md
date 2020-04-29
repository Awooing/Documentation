## Logging in and obtaining a token

```shell
curl "https://rest.awooing.moe/api/v1/user"
    -H "Content-Type: application/json"
    -d '{"username":"XxAwooerXx", "password":"1234"}'
```

```php

$credentials = [
    "username"=>"XxAwooerXx",
    "password"=>"1234" 
];

$options = [
    "http"=>[
        "method"=>"POST",
        "content"=>json_encode($credentials)
    ]
];

$context = stream_context_create($options);
$login = file_get_contents("https://rest.awooing.moe/api/v1/user", false, $context);
$json = json_decode($login);


// ... and then
echo $json->error; // prints the status code, in case of success it's "OK"
```

> The above command/code returns JSON structured like this:

```json
{
    "error": "OK",
    "token": "SessionIDToken"
}
```

> Error: 

```json
{
    "error": "ERR_CODE"
}
```

> Rate limited:

```json
{
    "error": "RATE_LIMITED",
    "try_again": 1588145975
}
```

This endpoint authenticates you and you can obtain the token.

<aside class="notice">
This endpoint is rate limited for 5 unsuccessful login attempts per IP address.<br>
If you get rate limited, you can use this endpoint (or login on the website) after 1 hour.
</aside>

### HTTP Request
`POST http://rest.awooing.moe/api/v1/user`

### JSON Response (successful login)
Key | Type | Description
--- | ---- | -----------
error | string | Always OK in case of a success
token | string | The Session ID token

### JSON Response (error)
Key | Type | Description
--- | ---- | -----------
error | string | Error status message

### JSON Response (rate limited)
Key | Type | Description
--- | ---- | -----------
error | string | Always RATE_LIMITED in case of being rate limited
try_again | int | Time before the IP may use this endpoint again

### Status Messages 
Message | Description
------- | -----------
OK      | The login was successful.
RATE_LIMITED | You have been rate limited.
ACC_NOT_FOUND | Account you tried to login with doesn't exist
ACC_WRONG_PASS | You have entered an incorrect password
ACC_NOT_VERIFIED | The account is not verified.

<aside class="notice">
You can login even when you are banned, however the API will become useless.
</aside>

<aside class="warning">
29/04/2020 - These status messages are likely to be changed soon.
</aside>


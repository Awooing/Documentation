## Registering an account

```shell
curl "https://rest.awooing.moe/api/v1/user"
    -X PUT
    -H "Content-Type: application/json"
    -d '{"username":"XxAwooerXx", "email": "awooer@awooing.moe", "password":"1234", "repeatpw":"1234"}'
```

```php

$credentials = [
    "username"=>"XxAwooerXx",
    "email"=>"awooer@awooing.moe",
    "password"=>"1234",
    "repeatpw"=>"1234" 
];

$options = [
    "http"=>[
        "method"=>"PUT",
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
    "httpCode": 123,
    "message": "status message"
}
```

> Rate limited:

```json
{
    "httpCode": 429,
    "message": "rate limited", 
    "try_again": 1588145975
}
```

This endpoint registers a new user.

<aside class="notice">
This endpoint is rate limited for 1 registration per IP address.
If you get rate limited, you can use this endpoint (or register on the website) after 1 hour.
</aside>

### HTTP Request
`PUT https://rest.awooing.moe/api/v1/user`

### JSON Response 
Key           | Type          | Description
------------- | ------------- | -------------
httpCode      | int           | HTTP Error Code
message       | string        | The Status Message

### JSON Response (rate limited)
Key           | Type          | Description
------------- | ------------- | -------------
httpCode      | int           | HTTP Error Code
message       | string        | The Status Message (always `rate limited`)
try_again     | string        | Time before the IP may use this endpoint again

### Status Messages 
HTTP Code | Message             | Description
--------- | ------------------- | -----------
200       | ok                  | The registration was successful
400       | invalid json        | Malformed JSON body
400       | invalid request     | Missing information in the JSON
400       | username taken      | The username you're trying to register is taken
400       | email used          | The email is already associated with another account
400       | password mismatch   | The values of `password` and `repeatpw` doesn't match
429       | rate limited        | You have been rate limited. Additional json key `try_again` is added.

# Errors

<aside class="warning">
If you come across error 500 or 503, please report it to <code>!Poi*Awoo Vottus#6543</code> (available on <a href="https://discordapp.com/invite/wolke">Awoo Community Discord</a>) or at <a href="mailto:vottus@awooing.moe">vottus@awooing.moe</a></aside>

We utilize the following HTTP error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- You are not logged in or missing auth token.
403 | Forbidden -- You are not allowed to go here.
404 | Not Found -- The endpoint doesn't exist or you didn't specify (or specified invalid) parameter like ID
405 | Method Not Allowed -- You tried a unsupported method.
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

# OAuth2 Server Admin Authentication

**Server Admin is a special role, distinct from Account Admin! You usually want to log in as an Account Admin (i.e. the user tagged as "ADMIN" in the Browser Client) instead; use the standard [OAuth2 Auth](OAuth2.md) to do so.**

To get started with the CoffeeCup API as the server admin, we need to retrieve an access token and a refresh token from the server. It can be retrieved with the `client_credentials` grant type.
HTTPS is required for accessing the API.

## Retrieving the tokens

We send the parameters as shown in the example below via `x-www-form-urlencoded` to `https://api.coffeecupapp.com/oauth2/token`.

[cURL](http://en.wikipedia.org/wiki/CURL) example (password is saved to console history!):

```sh
cc_client_id=CLIENT_ID
cc_client_secret=CLIENT_SECRET

curl -d "grant_type=client_credentials&client_id=$cc_client_id&client_secret=$cc_client_secret" \
-X POST https://api.coffeecupapp.com/oauth2/token
```

Response:

```json
{
  "token_type": "bearer",
  "access_token": "59d8cb89af1fc22a141066b8e71337c4abfee434",
  "expires_in": 3600,
  "refresh_token": "83ef27458d5e71337afe40b4854264cf72889cac"
}
```

The `access_token` can then be used for further authentication. In this example, it expires in 3600 seconds.
The `refresh_token` allows retrieving a new `access_token` without providing the username and password again:

```sh
cc_refresh_token=REFRESH_TOKEN
cc_client_id=CLIENT_ID
cc_client_secret=CLIENT_SECRET

curl \
  -d "grant_type=refresh_token&refresh_token=$cc_refresh_token&client_id=$cc_client_id&client_secret=$cc_client_secret" \
  -X POST https://api.coffeecupapp.com/oauth2/token
```

Response:

```json
{
  "token_type": "bearer",
  "access_token": "84dfa15357e02fa3f69a53ab51337a6eb7eaf80a",
  "expires_in": 3600,
  "refresh_token": "5b8ab71337de1f45c669cc7481f96fa9e111ec20"
}
```


## Making a request

To interact with the CoffeeCup API, we add the `access_token` via HTTP header to a request.

Please look at other sections for examples.

If there's an authentication error, we get a message like this:

```json
{
  "error": "E_FORBIDDEN",
  "status": 403,
  "summary": "Forbidden",
  "raw": "The access token provided is invalid."
}
```


## Misc

*Chrome Users*: Check out the [Postman REST Client](https://chrome.google.com/webstore/detail/postman-rest-client/fdmmgilgnpjigdojojpjoooidkmcomcm?hl=en) to test requests.

*Firefox Users*: We recommend using the [RestClient plugin](https://addons.mozilla.org/en-US/firefox/addon/restclient/) to help you make requests to and see responses from the CoffeeCup API.

*OS X*: We recommend [Paw](https://luckymarmot.com/paw).

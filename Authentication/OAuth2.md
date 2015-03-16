# OAuth2 Authentication

To get started with the CoffeeCup API, we need to retrieve an access token and a refresh token from the server. It can be retrieved using the username and password.
HTTPS is required for accessing the API.

## Retrieving the tokens

We send the parameters as shown in the example below via `x-www-form-urlencoded` to `https://company.coffeecupapp.com/v1/oauth2/token`.

[cURL](http://en.wikipedia.org/wiki/CURL) example (password is saved to console history!):

```sh
cc_username=USERNAME
cc_password=PASSWORD
cc_client_id=CLIENT_ID
cc_client_secret=CLIENT_SECRET

curl -d "grant_type=password&username=$cc_username&password=$cc_password&client_id=$cc_client_id&client_secret=$cc_client_secret" \
-X POST https://company.coffeecupapp.com/v1/oauth2/token
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
  -X POST https://company.coffeecupapp.com/v1/oauth2/token
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

In the following cURL example, we return the current user:

```sh
cc_access_token=ACCESS_TOKEN

curl \
  -H "Authorization: Bearer $cc_access_token" \
  -X GET https://company.coffeecupapp.com/v1/users/me
```

Response:

```json
{
  "user": {
    "account": 1,
    "status": 1,
    "firstname": "John",
    "lastname": "Doe",
    "email": "jd@example",
    /* ... */
  }
}
```

If there's an authentication error, we get a message like this:

```json
{
  "error": "E_FORBIDDEN",
  "status": 403,
  "summary": "Forbidden",
  "raw": "The access token provided is invalid."
}
```

## Password forgot

if we forget a passwort we can make CoffeeCup send us an e-mail with reset instructions. We just send a `passwordforgotrequest` via JSON containing the e-mail like in the following cURL example:

```sh
curl \
  -H "Content-Type: application/json" \
  -d '{
        "passwordforgotrequest":{
          "email":"user@example.com"
        }
      }' \
  https://company.coffeecupapp.com/v1/users/forgotPassword
```

## Misc

*Chrome Users*: Check out the [Postman REST Client](https://chrome.google.com/webstore/detail/postman-rest-client/fdmmgilgnpjigdojojpjoooidkmcomcm?hl=en) to test requests.

*Firefox Users*: We recommend using the [RestClient plugin](https://addons.mozilla.org/en-US/firefox/addon/restclient/) to help you make requests to and see responses from the CoffeeCup API.

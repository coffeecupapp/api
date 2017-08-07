# Admin API

These calls require us to be a Server Admin (see Authentication/OAuth2 Admin).

## Create a new account

`PUT /v1/admin/createAccount`

Example request

```shell
curl \
	-H "Authorization: Bearer ACCESS_TOKEN" \
	-X "PUT" "http://api.coffeecupapp.com/v1/admin/createAccount" \
	--data-urlencode "email=EMAIL" \
	--data-urlencode "lastname=LASTNAME" \
	--data-urlencode "domain=DOMAINNAME" \
	--data-urlencode "firstname=FIRSTNAME"
```
HTTP Response: 200 Success

```json
Account created.
```


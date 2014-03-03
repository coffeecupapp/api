# Users

## Get All Users

`GET /api/user`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/user
```

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "2",
    "user" : [
      {
        "id" : 1,
        "type_index" : 0,
        "date_format" : "d.m.Y",
        "beginning_of_week" : 0,
        "modified" : "2014-02-08 17:12:19",
        "lastname" : "nachname",
        "last_active_at" : "2014-02-08 17:12:19",
        "hourly_rate" : "90.9900",
        "image_url" : "",
        "firstname" : "vorname",
        "timeofday_format" : "H:i:s",
        "language" : "de_DE",
        "created" : "2014-02-08 17:12:19",
        "timezone" : "Europe/Berlin",
        "role_index" : 0,
        "last_login_at" : "2014-02-08 17:12:19",
        "email" : "1@2gu.de"
      },
      {
        ...
      }
    ]
  },
  "success" : true,
  "message" : "Record(s) Found"
}
```

## Get All User of a certain project (1)

`GET api/project/1/users`

## Grant a users (2) access to a certain project (1)

`PUT api/project/1/users/2`

## Revoke a users (2) access to a certain project (1)

`DELETE api/project/1/users/2`


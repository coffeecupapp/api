# Users

## Get My User

`GET /api/user/me`

Example request

```shell
curl -v -u admin:admin  \
    -H "Content-type: application/json" \
    -X GET http://dev.coffeecupapp.com/api/user/me
```

HTTP Response: 200 Success

```json
{
  "success" : true,
  "message" : "Record Found",
  "data" : {
    "totalCount" : "1",
    "user" :
      {
        "id" : 1,
        "type_index" : 0,
        "date_format" : "d.m.Y",
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
        "email" : "1@2gu.de",
        "beginning_of_week" : "monday",
        "hours_of_work": {
            "id" : 1,
            "user_id" : 1,
            "monday": 8,
            "tuesday": 8,
            "wednesday": 8,
            "thursday": 8,
            "friday": 4,
            "saturday": 0,
            "sunday": 0
        },
        "user_score": {
            "id" : 1,
            "user_id" : 1,
            "current_week": 1200,
            "current_month": 5690
        },
        "user_level": 5
      }
  }
}
```


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
        "email" : "1@2gu.de",
        "beginning_of_week" : "monday",
        "hours_of_work": {
            "id" : 1,
            "user_id" : 1,
            "monday": 8,
            "tuesday": 8,
            "wednesday": 8,
            "thursday": 8,
            "friday": 4,
            "saturday": 0,
            "sunday": 0
        },
        "user_score": {
            "id" : 1,
            "user_id" : 1,
            "current_week": 1200,
            "current_month": 5690
        },
        "user_level": 5
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

HTTP Response: 200 Success

## Grant a users (2) access to a certain project (1)

`PUT api/project/1/users/2`

HTTP Response: 200 Success

```json
{
    "success": "true",
    "message": "Subresource Added",
    "data": {
        ...
    }
}

## Revoke a users (2) access to a certain project (1)

`DELETE api/project/1/users/2`

HTTP Response: 200 Success

```json
{
    "success": "true",
    "message": "Sub-Resource Deleted",
    "data": {
        ...
    }
}
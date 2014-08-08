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
        "status" : 1,
        "type_index" : 0,
        "date_format" : "d.m.Y",
        "modified" : "2014-02-08 17:12:19",
        "lastname" : "nachname",
        "last_active_at" : "2014-02-08 17:12:19",
        "hourly_rate" : "90.9900",
        "image_type" : 0, // 0:default, 1:gravatar
        "firstname" : "vorname",
        "timeofday_format" : "H:i:s",
        "language" : "de_DE",
        "created" : "2014-02-08 17:12:19",
        "timezone" : "Europe/Berlin",
        "role_index" : 0,
        "last_login_at" : "2014-02-08 17:12:19",
        "email" : "email@provider.com",
        "beginning_of_week" : "monday",
        "hours_of_work": {
            "id" : 1,
            "user_id" : 1,
            "monday": "23.95",
            "tuesday": "23.00",
            "wednesday": "5.00",
            "thursday": "8.00",
            "friday": "7.00",
            "saturday": "2.00",
            "sunday": "0.00",
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
        ...
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

## Get Archived Users Only

`GET /api/user?filter=[{"property": "status", "value" : "0", "operator": "="}]`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Users (DEFAULT Behaviour)

`GET /api/user?filter=[{"property": "status", "value" : "0", "operator": ">="}]`

HTTP Response: 200 Success

## Get Non-Archived Users Only

`GET /api/user?filter=[{"property": "status", "value" : "1", "operator": "="}]`

HTTP Response: 200 Success

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

## Archive A User

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE USER

`PUT /api/user/#{user_id}`

```json
{
    "status": "0"
}
```
HTTP Response: 200 OK



## Upload A Profile Image

`POST /api/user/image/#{user_id}`

HTTP Response: 200 OK

When adding or updating an image, you don't need to post any JSON. Just post the image data like you would any multipart form data. Be sure to set the name of the post data to "upload" and set the "filename=" parameter:

```http
Host: #{yoursubdomain}.coffeecupapp.com
Authorization: Basic (insert your authentication string here)
Content-Length: 456221
Content-Type: multipart/form-data; boundary=------------------------------E19zNvXGzXaLvS5C
------------------------------E19zNvXGzXaLvS5C
Content-Disposition: form-data; name="upload"; filename="DSC00039.JPG"
Content-Type: image/jpeg

#{ BINARY IMAGE DATA }

------------------------------E19zNvXGzXaLvS5C
```

## GET The Users Profile Image

`GET /api/user/image/#{user_id}`

HTTP Response: 200 OK

Perform a simple GET on the Profile Image URL to receive the image data.


# Users

## Get My User

`GET /v1/users/me`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/users/me
```

HTTP Response: 200 Success

```json
{
  "user": {
    "status": 1,
    "firstname": "John",
    "lastname": "Doe",
    "email": "jd@example.com",
    "hourlyRate": 100,
    "dateFormat": "MM/DD/YYYY",
    // possible values: 'hh:mma'=TIME_FORMAT_12, 'HH:mm'=TIME_FORMAT_24
    "timeFormat": "hh:mma",
    // possible values: 0=hours:minutes, 1=decimal format
    "durationFormat": 1,
    "language": "de_DE",
    "timezone": "Europe/Berlin",
    // the key of the role model
    "role": 1,
    // possible values: 0=USER_TYPE_EMPLOYEE, 1=USER_TYPE_FREELANCER
    "typeIndex": 0,
    // possible values: "saturday", "sunday", "monday"
    "beginningOfWeek": "monday",
    // possible values: 0=UPLOAD, 1=GRAVATAR
    "imageType": 1,
    "userLevel": 2,
    // possible values: 0=PASSWORD_STATUS_NEEDS_SET,1=PASSWORD_STATUS_NEEDS_RESET, 2=PASSWORD_STATUS_OK
    "passwordStatus": 2,
    "showBudget": false,
    "showHours": true,
    "hoursMonday": 8,
    "hoursTuesday": null,
    "hoursWednesday": 8,
    "hoursThursday": null,
    "hoursFriday": 8,
    "hoursSaturday": null,
    "hoursSunday": null,
    // possible values: 0=NONE, 1=DAILY
    "hoursOfOfWorkType": 0,
    // possible values: 1=TIME_ENTRY_COLOR_TASK,2=TIME_ENTRY_COLOR_PROJECT, 3=TIME_ENTRY_COLOR_CLEAN
    "timeEntryBackgroundColor": 1,
    "visibleDaysPerWeek": 7,
    "holidaysPerYear": 28,
    "id": 5
  }
}
```

## Get All Users

`GET /v1/users`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/users
```

HTTP Response: 200 Success

```json
{
  "users": [
    {
      "role": 0,
      "status": 1,
      "firstname": "Ulf",
      "lastname": "Petersen",
      "email": "up@example.com",
      "hourlyRate": 100,
      "dateFormat": "MM/DD/YYYY",
      "timeFormat": "hh:mma",
      "durationFormat": 1,
      "language": "de_DE",
      "timezone": "Europe/Berlin",
      "role": 2,
      "typeIndex": 0,
      "beginningOfWeek": "monday",
      "imageType": 1,
      "userLevel": 9999,
      "passwordStatus": 2,
      "showBudget": true,
      "showHours": true,
      "hoursMonday": 8,
      "hoursTuesday": 8,
      "hoursWednesday": 8,
      "hoursThursday": 8,
      "hoursFriday": 8,
      "hoursSaturday": null,
      "hoursSunday": null,
      "hoursOfOfWorkType": 0,
      "timeEntryBackgroundColor": 1,
      "visibleDaysPerWeek": 7,
      "holidaysPerYear": 28,
      "id": 1
    },
    {
      "role": 0,
      "status": 1,
      "firstname": "Tina",
      "lastname": "Brot",
      "email": "tb@example.com",
      "hourlyRate": 99,
      "dateFormat": "MM/DD/YYYY",
      "timeFormat": "hh:mma",
      "durationFormat": 1,
      "language": "de_DE",
      "timezone": "Europe/Berlin",
      "role": 25,
      "typeIndex": 1,
      "beginningOfWeek": "monday",
      "imageType": 1,
      "userLevel": 11,
      "passwordStatus": 2,
      "showBudget": true,
      "showHours": true,
      "hoursMonday": 8,
      "hoursTuesday": null,
      "hoursWednesday": 8,
      "hoursThursday": null,
      "hoursFriday": 8,
      "hoursSaturday": null,
      "hoursSunday": null,
      "hoursOfOfWorkType": 1,
      "timeEntryBackgroundColor": 1,
      "visibleDaysPerWeek": 7,
      "holidaysPerYear": 28,
      "id": 2
    },
    /* ... 10 more ... */
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 12,
    "criteria": {}
  }
}
```

## Get Archived Users Only

`GET /v1/users?status[]=0`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Users (DEFAULT Behaviour)

`GET /v1/users?status[]=0&status[]=1`

HTTP Response: 200 Success

## Get Non-Archived Users Only

`GET /v1/users?status[]=1`

HTTP Response: 200 Success

## Get All User of a certain project (1)

`GET /v1/userAssignments?project[]=1`

For user-IDs 1, 3 and 37:

`GET /v1/users?id[]=1&id[]=3&id[]=37`

HTTP Response: 200 Success

## TODO: Grant a users (2) access to a certain project (1)

```
PUSH /v1/userassignments/

{
  "userAssignment": {
    "user": 2,
    "project": 1
  }
}
```

HTTP Response: 200 Success

```json
{
  "userAssignment": {
    "account": null,
    "user": 1,
    "project": 1,
    "role": null,
    "status": 1,
    "projectManager": null,
    "hourlyRate": null,
    "budgetHours": null,
    "showBudget": null,
    "showHours": null,
    "id": 45
  }
}
```

## Revoke a users (2) access to a certain project (1)

`GET /v1/userassignments/?user[]=1&project[]=2`

HTTP Responnse: 200 Success

```
{
  "userAssignments": [
    {
      "user": 1,
      "project": 2,
      "role": null,
      "status": 1,
      "projectManager": null,
      "hourlyRate": null,
      "budgetHours": null,
      "showBudget": null,
      "showHours": null,
      "id": 47 /* <------ use this ID */
    }
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 1,
    "criteria": {
      "user": "1",
      "project": "2"
    }
  }
}
```

`DELETE /v1/userassignments/47`

HTTP Response: 200 Success

```json
null
```

## Archive A User

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE USER

`PUT /v1/users/#{user_id}`

```json
{
  "user": {
    "status": "0"
  }
}
```
HTTP Response: 200 OK



## Upload A Profile Image

`POST /v1/files/upload/user_image/#{user_id}`

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

`GET /v1/files/get/user_image/#{user_id}/#{size}.#{format}`

```
size: s, m, l
format: jpg, png
```


HTTP Response: 200 OK

Perform a simple GET on the Profile Image URL to receive the image data.

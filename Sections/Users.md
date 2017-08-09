# Users

## Constants for enum fields

### status

- `0` - User archived
- `1` - User active

### dateFormat

- `"MM/DD/YYYY"` - 05/25/2017
- `"DD/MM/YYYY"` - 25/05/2017
- `"YYYY-MM-DD"` - 2017-05-25
- `"DD.MM.YYYY"` - 25.05.2017
- `"YYYY.MM.DD"` - 2015.05.25
- `"YYYY/MM/DD"` - 2015/05/25

### timeFormat

- `"hh:mma"` - 03:45pm
- `"HH:mm"` - 15:45

### durationFormat

- `0` - 1:30 (hours:minutes)
- `1` - 1.50 (hours in decimal format)

### beginningOfWeek

- `saturday`
- `sunday`
- `monday`

### imageType

- `0` - Uploaded avatar image
- `1` - Avatar should be pulled from Gravatar

### passwordStatus
 
- `0` - Password needs to be set
- `1` - Password needs to be reset
- `2` - A valid password is valid

### timeEntryBackgroundColor

- `1` - Color of TimeEntry based on [Task](Tasks.md)
- `2` - Color of TimeEntry based on [Project](Projects.md)
- `3` - Styling is independent of Task / Project


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
    "timeFormat": "hh:mma",
    "durationFormat": 1,
    "language": "en_EN",
    "timezone": "Europe/Berlin",
    "uiState": "/** … **/",
    "beginningOfWeek": "monday",
    "imageType": 2,
    "passwordStatus": 2,
    "vacationDaysPerYear": 28,
    "imageFileToken": "GohinyByt4DyVRbERWPyD9txjfhXNx_2sJgY3e9c541aQI4ZduYAI1VoTYTp31tP",
    "imageDirectoryURL": "http://localhost:1337/v1/files/get/user_image/GohinyByt4DyVRbERWPyD9txjfhXNx_2sJgY3e9c541aQI4ZduYAI1VoTYTp31tP/",
    "allowConcurrentTimeEntries": false,
    "favorite": false,
    "emailHmacHash": "b098a1c3f9c59e4611c105b4d6927ef9be08837bce5879603a4eb991927ca2a4",
    "jobLabel": null,
    "department": null,
    "bankName": null,
    "ibanNumber": null,
    "bicNumber": null,
    "insuranceName": null,
    "insuranceType": null,
    "street": null,
    "city": null,
    "postCode": null,
    "country": "DE",
    "birthplace": null,
    "birthday": null,
    "mobileNumber": null,
    "phoneNumber": null,
    "privateEmail": null,
    "faxNumber": null,
    "id": 5,
    "idHashed": "GohinyByt4DyVRbERWPyD9txjfhXNx_2sJgY3e9c541aQI4ZduYAI1VoTYTp31tP",
    "visibleDaysPerWeek": 7,
    "timeEntryBackgroundColor": 1,
    /** There are also fields from the currently valid UserEmployment included **/
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
    "status": 1,
    "firstname": "John",
    "lastname": "Doe",
    "email": "jd@example.com",
    "hourlyRate": 100,
    "dateFormat": "MM/DD/YYYY",
    "timeFormat": "hh:mma",
    "durationFormat": 1,
    "language": "en_EN",
    "timezone": "Europe/Berlin",
    "uiState": "/** … **/",
    "beginningOfWeek": "monday",
    "imageType": 2,
    "passwordStatus": 2,
    "vacationDaysPerYear": 28,
    "imageFileToken": "GohinyByt4DyVRbERWPyD9txjfhXNx_2sJgY3e9c541aQI4ZduYAI1VoTYTp31tP",
    "imageDirectoryURL": "https://cdn.coffeecupapp.com/user_image/GohinyByt4DyVRbERWPyD9txjfhXNx_2sJgY3e9c541aQI4ZduYAI1VoTYTp31tP/s.png",
    "allowConcurrentTimeEntries": false,
    "favorite": false,
    "emailHmacHash": "b098a1c3f9c59e4611c105b4d6927ef9be08837bce5879603a4eb991927ca2a4",
    "jobLabel": null,
    "department": null,
    "bankName": null,
    "ibanNumber": null,
    "bicNumber": null,
    "insuranceName": null,
    "insuranceType": null,
    "street": null,
    "city": null,
    "postCode": null,
    "country": "DE",
    "birthplace": null,
    "birthday": null,
    "mobileNumber": null,
    "phoneNumber": null,
    "privateEmail": null,
    "faxNumber": null,
    "id": 5,
    "idHashed": "GohinyByt4DyVRbERWPyD9txjfhXNx_2sJgY3e9c541aQI4ZduYAI1VoTYTp31tP",
    "visibleDaysPerWeek": 7,
    "timeEntryBackgroundColor": 1,
    /** There are also fields from the currently valid UserEmployment included **/
  },
    {
    "status": 1,
    "firstname": "Jane",
    "lastname": "Smith",
    "email": "js@example.com",
    "hourlyRate": 100,
    "dateFormat": "MM/DD/YYYY",
    "timeFormat": "hh:mma",
    "durationFormat": 1,
    "language": "en_EN",
    "timezone": "Europe/Berlin",
    "uiState": "/** … **/",
    "beginningOfWeek": "monday",
    "imageType": 2,
    "passwordStatus": 2,
    "vacationDaysPerYear": 28,
    "imageFileToken": null,
    "imageDirectoryURL": null,
    "allowConcurrentTimeEntries": false,
    "favorite": false,
    "emailHmacHash": "16a32f42d2cd831c83e3759127f11c789dcf703f2e25f75dab0e0d40ab668388",
    "jobLabel": null,
    "department": null,
    "bankName": null,
    "ibanNumber": null,
    "bicNumber": null,
    "insuranceName": null,
    "insuranceType": null,
    "street": null,
    "city": null,
    "postCode": null,
    "country": "DE",
    "birthplace": null,
    "birthday": null,
    "mobileNumber": null,
    "phoneNumber": null,
    "privateEmail": null,
    "faxNumber": null,
    "id": 6,
    "idHashed": null,
    "visibleDaysPerWeek": 7,
    "timeEntryBackgroundColor": 1,
    /** There are also fields from the currently valid UserEmployment included **/
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

## Assignments to Projects

Assignments to projects are managed through [User Assignments](User%20Assignments.md). 

## Employment Information

Information on the employment arrangements is managed through [User Employments](User%20Employments.md)

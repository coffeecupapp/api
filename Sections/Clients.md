# Clients

## Get All Clients

`GET /v1/users`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/clients
```
HTTP Response: 200 Success

```json
{
  "clients": [
    {
      "status": 0, # Client is archived
      "name": "Mustermann-Soft AG",
      "website": "www.example.com",
      "code": "mms",
      "hourlyRate": 90,
      "imageType": 0,
      "createdAt": "2014-07-25T14:07:54.000Z",
      "updatedAt": "2016-03-21T01:00:00.000Z",
      "id": 1
    },
    {
      "status": 1, # Client is active
      "name": "Musterfrau-Auto GmbH",
      "website": "www.example.com",
      "code": "mfa",
      "hourlyRate": 110,
      "imageType": 0,
      "createdAt": "2015-10-12T16:15:29.000Z",
      "updatedAt": "2017-07-25T11:07:54.000Z",
      "id": 2
    },
    {
      "status": 1,
      "name": "Musterkind-Toys GbR",
      "website": "www.example.com",
      "code": "mkt",
      "hourlyRate": 50,
      "imageType": 0,
      "createdAt": "2017-03-10T11:43:15.000Z",
      "updatedAt": "2017-07-27T14:07:54.000Z",
      "id": 3
    },
    /* ... */
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 13,
    "criteria": {}
  }
}
```

### You can filter by modified. To show only the clients that have been updated since "2013-01-01 17:23", pass the UTC date value (URL encoded).

`GET /v1/clients?where={"updatedAt":{">=": "2013-01-01 17:23"}}`

HTTP Response: 200 Success

## Get Archived Clients Only

`GET /v1/clients?status[]=0`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Clients (DEFAULT Behaviour)

`GET /v1/clients?status[]=0&status[]=1`

HTTP Response: 200 Success

## Get Non-Archived Clients Only

`GET /v1/clients?status[]=1`

HTTP Response: 200 Success


## Get A Client

`GET /v1/clients/#{client_id}`

HTTP Response: 200 Success

## Create A New Client

`POST /v1/clients`

HTTP Response: 201 Created

You need to post the following:

```json
{
  "client": {
    "name": "Ultra Motorradreifen UG (haftungsbeschränkt)"
  }
}
```

## Update A Client

`PUT /v1/clients/#{client_id}`

HTTP Response: 200 OK

You may update selected attributes for a client.

```json
{
  "client": {
    "name": "Ultra Motorradreifen GmbH"
  }
}
```


## Archive A Client

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE CLIENT

`PUT /v1/clients/#{client_id}`

```json
{
  "client": {
    "status": 0
  }
}
```
HTTP Response: 200 OK

## Delete A Client

`DELETE /v1/clients/#{client_id}`

If client does not have associated projects and/or time entries CoffeeCup deletes it and returns
HTTP Response: 200 OK

otherwise client is not deleted and you'll get a HTTP Response: 500 Could not delete model.


## Upload A Client Image

`POST /v1/files/upload/client_image/#{user_id}`

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

## GET The Client's Profile Image

`GET /v1/files/get/client_image/#{user_id}/#{size}.#{format}`

```
size: s, m, l
format: jpg, png
```


HTTP Response: 200 OK

Perform a simple GET on the Client Image URL to receive the image data.

# Clients

## Get All Clients

`GET /api/client`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/client
```

HTTP Response: 200 Success

```json
{
    "success":true,
    "message":"Record(s) Found",
    "data":{
        "totalCount":"10",
        "client":[{
            "id":"1",
            "status": 1,
            "hourly_rate":"90.9900",
            "name":"Client 1",
            "code": "CL1",
            "created":"0000-00-00 00:00:00",
            "modified":"0000-00-00 00:00:00",
            "currency":"EUR",
            "projects":[{
                "id":"1",
                "client_id":"1",
                "name":"Projekt 1",
                "invoice_type_index":null,
                "budget_type_index":null,
                "comment":null,
                "code":"PR1",
                "hourly_rate":"90.0000",
                "budget":"900000.0000",
                "created":"0000-00-00 00:00:00",
                "modified":"0000-00-00 00:00:00"
            },{
            ...
            }],
            "contacts":[{
                "id":"1",
                "client_id":"1",
                "country":"DE",
                "firstname":"Vorname",
                "lastname":"Nachname",
                "title":"Dr.",
                "email":"email@provider.com",
                "phone":"1234",
                "phone_mobile":"1212121",
                "fax":null,
                "address1":null,
                "address2":null,
                "postcode":null,
                "city":null,
                "comment":null,
                "created":"0000-00-00 00:00:00",
                "modified":"0000-00-00 00:00:00"
            }]
        },{
        ...
        }]
    }
}
```

### You can filter by modified. To show only the clients that have been updated since "2013-01-01 17:23", pass the UTC date value (URL encoded).

`GET /api/client?filter=[{"property": "modified", "value" : "2013-01-01 17:23", "operator": ">="}]`

HTTP Response: 200 Success

### You can filter by created. To show only the clients that have been created between "2013-01-01" and "2015-01-31", pass these values (URL encoded).

`GET /api/client?filter=[{"property": "created", "value" : "2013-01-01", "operator": ">="} , {"property": "created", "value" : "2015-01-31", "operator": "<="}]`

HTTP Response: 200 Success


## Get Archived Clients Only

`GET /api/client?filter=[{"property": "status", "value" : "0", "operator": "="}]`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Clients (DEFAULT Behaviour)

`GET /api/client?filter=[{"property": "status", "value" : "0", "operator": ">="}]`

HTTP Response: 200 Success

## Get Non-Archived Clients Only

`GET /api/client?filter=[{"property": "status", "value" : "1", "operator": "="}]`

HTTP Response: 200 Success


## Get A Client

`GET /api/client/#{client_id}`

HTTP Response: 200 Success

```json
{
    "success":true,
    "message":"Record(s) Found",
    "data":{
        "totalCount":"10",
        "client":{
            "id":"1",
            "currency_id":"1",
            "name":"Client 1",
            ...
        }
    }
}

```

## Create A New Client

`POST /api/client`

HTTP Response: 201 Created

You need to post the following:

```json
{
    "currency_id": 1,
    "name": "Client xy",
    "contacts": [{
        "country_id": "1",
        "firstname": "Vorname 4",
        "lastname": "Nachname 4",
        "title": null,
        "email": "foo@bar.com",
        "phone": 12121212,
        "phone_mobile": null,
        "fax": null,
        "address1": null,
        "address2": null,
        "postcode": null,
        "city": null,
        "comment": null,
        "created": "2014-02-09 17:23:51",
        "modified": "2014-02-09 17:23:51"
    },
    {
        ...
    }]
}
```

## Update A Client

`PUT /api/client/#{client_id}`

HTTP Response: 200 OK

You may update selected attributes for a client.

```json
{
    "name": "Clients new Name"
}
```


## Archive A Client

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE CLIENT

`PUT /api/client/#{client_id}`

```json
{
    "status": "0"
}
```
HTTP Response: 200 OK

## Delete A Client

`DELETE /api/client/#{client_id}`

If client does not have associated projects and/or time entries CoffeeCup deletes it and returns
HTTP Response: 200 OK

otherwise client is not deleted and you'll get a HTTP Response: 500 Could not delete model.

```json
{
    "success": false,
    "message": "Could not delete model",
    "data": {
        "errorCode": 500,
        "message": "Could not delete model"
    }
}
```

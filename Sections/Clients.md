# Clients

## Get All Clients

`GET /api/clients`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/clients
```

HTTP Response: 200 Success

```json
{
    "success": true,
    "message": "Record(s) Found",
    "data": {
        "meta": {
            "total": 3
        },
        "clients": [
            {
                "id": 1,
                "currency_id": 1,
                "name": "Client 1",
                "created": "2014-02-09 17:23:51",
                "modified": "2014-02-09 17:23:51",
                "currency": {
                    "id": 1,
                    "label": "EUR",
                    "symbol": "€"
                },
                "projects": [
                    1,
                    2,
                    4
                ],
                "contacts": [
                    1,
                    2
                ]
            },
            {
                ...
            }
        ],
        "projects": [
            {
                "id": 1,
                "client_id": 1,
                "name": "Projekt 1",
                "invoice_type_index": null,
                "budget_type_index": null,
                "comment": null,
                "code": "PR1",
                "hourly_rate": 90,
                "budget": 900000,
                "created": "2014-02-09 17:23:51",
                "modified": "2014-02-09 17:23:51"
            },
            {
                ...
            }
        ],
        "contacts": [
            {
                "id": 1,
                "reference_id": 1,
                "country_id": 1,
                "firstname": "Vorname",
                "lastname": "Nachname",
                "title": "Dr.",
                "email": "1@2gu.de",
                "phone": 1234,
                "phone_mobile": 1212121,
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
            }
        ]
    }
}
```

You can filter by modified. To show only the clients that have been updated since "2013-01-01 17:23", pass the UTC date value (URL encoded).

`GET /api/clients?filter=[{"property": "modified", "value" : "2013-01-01 17:23", "operator": ">="}]`

HTTP Response: 200 Success

You can filter by created. To show only the clients that have been created between "2013-01-01" and "2015-01-31", pass these values (URL encoded).

`GET /api/clients?filter=[{"property": "created", "value" : "2013-01-01", "operator": ">="} , {"property": "created", "value" : "2015-01-31", "operator": "<="}]`

HTTP Response: 200 Success


## Get A Client

GET `/api/clients/#{client_id}`

HTTP Response: 200 Success

```json
{
    "success": true,
    "message": "Record Found",
    "data": {
        "meta": {
            "total": 1
        },
        "client": {
            "id": 1,
            "currency_id": 1,
            "name": "Client 1",
            "created": "2014-02-09 17:23:51",
            "modified": "2014-02-09 17:23:51",
            "currency": {
                "id": 1,
                "label": "EUR",
                "symbol": "€"
            },
            "projects": [
                1,
                2,
                4
            ],
            "contacts": [
                1,
                2
            ]
        },
        "projects": [
            {
                "id": 1,
                "client_id": 1,
                "name": "Projekt 1",
                "invoice_type_index": null,
                "budget_type_index": null,
                "comment": null,
                "code": "PR1",
                "hourly_rate": 90,
                "budget": 900000,
                "created": "2014-02-09 17:23:51",
                "modified": "2014-02-09 17:23:51"
            },
            {
                ...
            }
        ],
        "contacts": [
            {
                "id": 1,
                "reference_id": 1,
                "country_id": 1,
                "firstname": "Vorname",
                "lastname": "Nachname",
                "title": "Dr.",
                "email": "1@2gu.de",
                "phone": 1234,
                "phone_mobile": 1212121,
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
            }
        ]
    }
}
```

## Create A New Client

`POST /api/clients`

HTTP Response: 201 Created

You need to post the following:

```json
{
	"client": {
        "currency_id": 1,
        "name": "Client xy",
        "contacts": [{
            "country_id": "1",
            "firstname": "Vorname 4",
            "lastname": "Nachname 4",
            "title": null,
            "email": "2@2gu.de",
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
}
```

## Update A Client

`PUT /api/clients/#{client_id}`

HTTP Response: 200 OK

You may update selected attributes for a client.

```json
{
	"client": {
        "name": "Clients new Name"
    }
}
```

## Delete A Client

`DELETE /api/clients/#{client_id}`

If client does not have associated projects or invoices CoffeeCup deletes it and returns HTTP Response: 200 OK otherwise client is not deleted and you'll get a HTTP Response: 400 Bad Request .

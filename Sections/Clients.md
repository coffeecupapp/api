# Clients

## GET ALL CLIENTS

GET `/api/clients`

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
                "id": 2,
                "currency_id": 1,
                "name": "Client 2",
                "currency": {
                    "id": 1,
                    "label": "EUR",
                    "symbol": "€"
                },
                "projects": [
                    3
                ],
                "contacts": [
                    3
                ]
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
                "budget": 900000
            },
            {
                "id": 2,
                "client_id": 1,
                "name": "Projekt 2",
                "invoice_type_index": null,
                "budget_type_index": null,
                "comment": null,
                "code": "PR2",
                "hourly_rate": 90,
                "budget": 10000
            },
            {
                "id": 4,
                "client_id": 1,
                "name": "Projekt 4",
                "invoice_type_index": null,
                "budget_type_index": null,
                "comment": null,
                "code": "PR4",
                "hourly_rate": 90,
                "budget": 500000
            },
            {
                "id": 3,
                "client_id": 2,
                "name": "Projekt 3",
                "invoice_type_index": null,
                "budget_type_index": null,
                "comment": null,
                "code": "PR3",
                "hourly_rate": 85.9,
                "budget": 50000
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
                "comment": null
            },
            {
                "id": 2,
                "reference_id": 1,
                "country_id": 1,
                "firstname": "Vorname 2",
                "lastname": "Nachname 2",
                "title": null,
                "email": "2@2gu.de",
                "phone": 12121212,
                "phone_mobile": null,
                "fax": null,
                "address1": null,
                "address2": null,
                "postcode": null,
                "city": null,
                "comment": null
            },
            {
                "id": 3,
                "reference_id": 2,
                "country_id": 1,
                "firstname": "Vorname",
                "lastname": "Nachname",
                "title": null,
                "email": "3@2gu.de",
                "phone": null,
                "phone_mobile": null,
                "fax": null,
                "address1": null,
                "address2": null,
                "postcode": null,
                "city": null,
                "comment": null
            },
            {
                "id": 4,
                "reference_id": 3,
                "country_id": 1,
                "firstname": "Vorname",
                "lastname": "Nachname",
                "title": null,
                "email": "4@2gu.de",
                "phone": null,
                "phone_mobile": null,
                "fax": null,
                "address1": null,
                "address2": null,
                "postcode": null,
                "city": null,
                "comment": null
            }
        ]
    }
}
```

You can filter by updated_since. To show only the clients that have been updated since "2010-09-25 18:30", pass the UTC date time value (URL encoded).

GET `/clients?updated_since=2010-09-25+18%3A30`

HTTP Response: 200 Success

## GET A CLIENT

GET `/clients/#{client_id}`

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
                "budget": 900000
            },
            {
                "id": 2,
                "client_id": 1,
                "name": "Projekt 2",
                "invoice_type_index": null,
                "budget_type_index": null,
                "comment": null,
                "code": "PR2",
                "hourly_rate": 90,
                "budget": 10000
            },
            {
                "id": 4,
                "client_id": 1,
                "name": "Projekt 4",
                "invoice_type_index": null,
                "budget_type_index": null,
                "comment": null,
                "code": "PR4",
                "hourly_rate": 90,
                "budget": 500000
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
                "comment": null
            },
            {
                "id": 2,
                "reference_id": 1,
                "country_id": 1,
                "firstname": "Vorname 2",
                "lastname": "Nachname 2",
                "title": null,
                "email": "2@2gu.de",
                "phone": 12121212,
                "phone_mobile": null,
                "fax": null,
                "address1": null,
                "address2": null,
                "postcode": null,
                "city": null,
                "comment": null
            }
        ]
    }
}
```

## CREATE A NEW CLIENT

POST `/clients`

HTTP Response: 201 Created

Location: /clients/#{new_client_id}

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
            "comment": null
        },
        {
            "country_id": "1",
            "firstname": "Vorname 5",
            "lastname": "Nachname 5",
            "title": null,
            "email": "2@2gu.de",
            "phone": 12121212,
            "phone_mobile": null,
            "fax": null,
            "address1": null,
            "address2": null,
            "postcode": null,
            "city": null,
            "comment": null
        }]
    }
}
```

## UPDATE CLIENT

PUT `/clients/#{client_id}`

HTTP Response: 200 OK

Location: /clients/#{client_id}

You may update selected attributes for a client.

```json
{
	"client": {
        "name": "Clients new Name"
    }
}
```

## DELETE A CLIENT

DELETE `/clients/#{client_id}`

If client does not have associated projects or invoices CoffeeCup deletes it and returns HTTP Response: 200 OK otherwise client is not deleted and you'll get a HTTP Response: 400 Bad Request .

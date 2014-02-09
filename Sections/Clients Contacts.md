# Clients

## Get All Contacts Of A Client

`GET /api/clients/#{client_id}/contacts`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/clients/1/contacts
```

HTTP Response: 200 Success

```json
{
    "success": true,
    "message": "Record(s) Found",
    "data": {
        "contacts": [
            {
                "id": 1,
                "client_id": 1,
                "country_id": 1,
                "firstname": "Vorname",
                "lastname": "Nachname",
                "title": "Dr.",
                "email": "1@2gu.de",
                "phone": "123/232324",
                "phone_mobile": "123/23234",
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
        ],
        "meta": {
            "total": 2
        }
    }
}
```

## Create A New Clients Contact

`POST /api/clients/#{client_id}/contacts`

HTTP Response: 201 Created

You need to post the following:

```json
{
    "contact": {
            "country_id": "1",
            "firstname": "Vorname 4",
            "lastname": "Nachname 4",
            "title": "Dr.",
            "email": "2@2gu.de",
            "phone": "089/121212",
            "phone_mobile": "089/121212",
            "fax": "089/121212",
            "address1": "Kanalstr. 15",
            "address2": "EG",
            "postcode": "80538",
            "city": "München",
            "comment": "Neuer Ansprechpartner"
    }
}
```

## Update A Clients Contact

`PUT /api/clients/#{client_id}/contacts/#{contact_id}`

HTTP Response: 200 OK

You may update selected attributes for a contact.

```json
{
    "contact": {
        "address1": "Isartorplatz. 3",
        "city": "München"
    }
}
```

## Delete A Contact

`DELETE /api/clients/#{client_id}/contacts/#{contact_id}`

HTTP Response: 200 OK

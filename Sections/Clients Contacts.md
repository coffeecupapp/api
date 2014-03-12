# Clients

## Get All Contacts Of A Client

`GET  /api/client/#{client_id}/contacts`
`GET  /api/contact?filter=[{"property": "client_id", "value" : #{client_id}}]`

Example request

```shell
curl -G -v -u admin:admin  \
	-H "Content-type: application/json" \
	--data-urlencode "filter=[{property:'client_id',value:1}]" \
	-X GET "http://api.coffeecup.local/api/contact"

```

HTTP Response: 200 Success

```json
{
    success: true,
    message: "Record(s) Found",
    data: {
        totalCount: "2",
        "contact": [
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
        ]
    }
}
```

## Create A New Clients Contact

`POST /api/contact`

HTTP Response: 201 Created

You need to post the following:

```json
{
    "client_id": "1",
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
```

## Update A Clients Contact

`PUT /api/contact/#{contact_id}`

HTTP Response: 200 OK

You may update selected attributes for a contact.

```json
{
    "address1": "Isartorplatz. 3",
    "city": "München"
}
```

## Delete A Contact

`DELETE /api/contact/#{contact_id}`

HTTP Response: 200 OK

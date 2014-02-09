# Currencies

## Get All Currencies

`GET /api/currencies`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/currencies
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
        "currencies": [
        ...
        ]
    }
}
```


## TBD....
FIND corresponding `PUT` `POST` and `DELETE` Requests in the clients sections
 [Clients API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients.md)
 [Client-Contacts API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients%20Contacts.md)
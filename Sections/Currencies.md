# Currencies

## Get All Currencies

`GET /api/currency`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/currency
```

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "1",
    "currency" : [
      {
        "symbol" : "€",
        "id" : 1,
        "created" : "0000-00-00 00:00:00",
        "label" : "EUR",
        "modified" : "0000-00-00 00:00:00"
      }
    ]
  },
  "success" : true,
  "message" : "Record(s) Found"
}
```


## TBD....
FIND corresponding `PUT` `POST` and `DELETE` Requests in the clients sections
 [Clients API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients.md)
 [Client-Contacts API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients%20Contacts.md)
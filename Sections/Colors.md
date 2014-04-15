# Colors

## Get All Colors

`GET /api/color`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/color
```

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "8",
    "color" : [
      {
          "id": 1,
          "label": "red",
          "hex": "ff0000"
     },
     ...
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
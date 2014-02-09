# Projects

## Get All Projects

`GET /api/projects`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/projects
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
        "projects": [
        ...
        ]
    }
}
```


## Get All Time Entries Of A Project

`GET /api/projects/1/time_entries`

## Get All Expenses Of A Project

`GET /api/projects/1/expenses`


## TBD....
FIND corresponding `PUT` `POST` and `DELETE` Requests in the clients sections
 [Clients API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients.md)
 [Client-Contacts API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients%20Contacts.md)
# Time Tracking

## Get All Time Entries

`GET /api/time_entries`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/time_entries
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
        "time_entries": [
            {
                "id": 21,
                "starttime": "2014-02-08 22:50:40",
                "endtime": "2014-02-08 22:55:30",
                "task_id": 10,
                "project_id": 3,
                "user_id": 2,
                "comment": "neuer asasdaddasd kommentar",
                "created": "2014-02-08 22:56:26",
                "modified": "2014-02-08 22:56:26",
                "task": {
                    "id": 10,
                    "label": "meeting",
                    "hourly_rate": 90,
                    "billable_default": 1,
                    "category_id": 1,
                    "created": "2014-02-08 22:56:26",
                    "modified": "2014-02-08 22:56:26"
                }
            },
            {
                ...
            }
        ]
    }
}
```

You can filter by starttime. To show only the time_entries that have a starttime after "2013-01-01 17:23", pass the UTC date value (URL encoded).

GET `/api/time_entries?filter=[{"property": "starttime", "value" : "2013-01-01 17:23", "operator": ">="}]`

HTTP Response: 200 Success

You can filter by starttime and endtime. To show only the time_entries that have been starttime between "2013-01-01" and endtime "2015-01-31", pass these values (URL encoded).

GET `/api/time_entries?filter=[{"property": "starttime", "value" : "2013-01-01", "operator": ">="} , {"property": "endtime", "value" : "2015-01-31", "operator": "<="}]`

HTTP Response: 200 Success

## TBD....
FIND corresponding `PUT` `POST` and `DELETE` Requests in the clients sections
 [Clients API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients.md)
 [Client-Contacts API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients%20Contacts.md)
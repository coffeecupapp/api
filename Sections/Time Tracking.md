# Time Tracking

## Get All Time Entries

`GET /api/time_entry`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/time_entry
```

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "22",
    "time_entry" : [
      {
        "starttime" : "2014-02-08 22:50:40",
        "id" : 1,
        "task" : {
          "id" : 1,
          "hourly_rate" : "90.9900",
          "category_id" : 1,
          "created" : "2014-02-08 22:35:00",
          "label" : "code",
          "billable_default" : 1,
          "modified" : "2014-02-08 22:35:00"
        },
        "task_id" : 1,
        "created" : "2014-02-08 22:54:40",
        "user_id" : 1,
        "endtime" : "2014-02-08 22:54:40",
        "project_id" : 1,
        "comment" : "neuerer kommentar",
        "modified" : "2014-02-08 22:54:40"
      },
      {
        ...
      }
    ]
  },
  "success" : true,
  "message" : "Record(s) Found"
}
```

## Get time entries by project
To show only the time_entries of a certain project, pass the GET Params (URL encoded).

`GET /api/time_entry?filter=[{"property": "project_id", "value" : "1"}]`

HTTP Response: 200 Success

## Get time entries by user
To show only the time_entries of a certain user, pass the GET Params (URL encoded).

`GET /api/time_entry?filter=[{"property": "user_id", "value" : "1"}]`

HTTP Response: 200 Success

## Get time entries by user AND project
To show the time_entries of a certain user and project, combine the above (URL encoded).

`GET /api/time_entry?filter=[{"property": "user_id", "value" : "2"},{"property": "project_id", "value" : "2"}]`

HTTP Response: 200 Success

## Get time entries by starttime
To show only the time_entries that have a starttime after "2013-01-01 17:23", pass the UTC date value (URL encoded).

`GET /api/time_entry?filter=[{"property": "starttime", "value" : "2013-01-01 17:23", "operator": ">="}]`

HTTP Response: 200 Success

## Get time entries by starttime and endtime.
To show only the time_entries that have been starttime between "2013-01-01" and endtime "2015-01-31", pass these values (URL encoded).

`GET /api/time_entry?filter=[{"property": "starttime", "value" : "2013-01-01", "operator": ">="} , {"property": "endtime", "value" : "2015-01-31", "operator": "<="}]`

HTTP Response: 200 Success

## Create a new time entry

`POST /api/time_entry`

HTTP Response: 201 Created

You may post the following

```json
{
    "starttime" : "2014-02-08 22:50:40",
    "task_id" : 1,
    "user_id" : 1,
    "endtime" : "2014-02-08 22:54:40",
    "project_id" : 1,
    "comment" : "neuerer kommentar"
}
```

## Update a time entry

`POST /api/time_entry/#{time_entry_id}`

HTTP Response: 200 OK

You may update selected attributes for a client.

```json
{
    "endtime" : "2014-02-08 22:59:00"
}

````

## Delete a time entry

`DELETE /api/time_entry/1`

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "1",
    "time_entry" : {
      "starttime" : "",
      "id" : 1,
      "task_id" : 1,
      "created" : "2014-02-08 22:31:18",
      "user_id" : 1,
      "endtime" : "",
      "project_id" : 1,
      "comment" : "neuerer kommentar",
      "modified" : {
        "params" : [],
        "expression" : "NOW()"
      }
    }
  },
  "success" : "true",
  "message" : "Record Deleted"
}
```



## TBD....
FIND corresponding `PUT` `POST` and `DELETE` Requests in the clients sections
 [Clients API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients.md)
 [Client-Contacts API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients%20Contacts.md)
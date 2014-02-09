# Tasks

## Get All Tasks

`GET /api/tasks`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/tasks
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
        "tasks": [
        ...
        ]
    }
}
```


# Task Categories

## Get All Task Categories

`GET /api/task_categories`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/task_categories
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
        "task_categories": [
        ...
        ]
    }
}
```


## TBD....
FIND corresponding `PUT` `POST` and `DELETE` Requests in the clients sections
 [Clients API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients.md)
 [Client-Contacts API](http://git.reppa.net/coffeecup/api_docs/blob/master/Sections/Clients%20Contacts.md)
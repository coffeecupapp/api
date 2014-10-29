# UserScore

## Get All User-Score Entries

`GET /api/user_score`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/task
```

HTTP Response: 200 Success

```json
{
    "success": true,
    "message": "Record(s) Found",
    "data": {
        "totalCount": 3,
        "user_score": [
            {
                "id": 1,
                "user_id": 1,
                "date": "2014-05-17",
                "score": 55,
                "percent": 77,
                "createdAt": "2014-05-17 00:03:02",
                "updatedAt": "2014-05-17 02:02:22",
                "status": 1
            },
            ...
        ]
    }
}
```

## Get User-Score Entries Of A Certain User

`GET /api/user_score?filter=[{"property": "user_id", "value" : "1", "operator": "="}]`

HTTP Response: 200 Success

## Get User-Score Entries For A Given Timeframe ##

`GET /api/user_score?filter=[{"property": "date", "value" : "2014-05-16", "operator": ">="} , {"property": "date", "value" : "2014-05-18", "operator": "<="}]`

HTTP Response: 200 Success

## Combine the Above

`GET /api/user_score?filter=[{"property": "user_id", "value" : "1", "operator": "="}, {"property": "date", "value" : "2014-05-16", "operator": ">="}, {"property": "date", "value" : "2014-05-18", "operator": "<="}]`

HTTP Response: 200 Success

## Get Archived User-Score Entries Only

`GET /api/user_score?filter=[{"property": "status", "value" : "0", "operator": "="}]`

HTTP Response: 200 Success

## Get Archived AND Non-Archived User-Score Entries (DEFAULT Behaviour)

`GET /api/user_score?filter=[{"property": "status", "value" : "0", "operator": ">="}]`

HTTP Response: 200 Success

## Get Non-Archived User-Score Entries Only

`GET /api/user_score?filter=[{"property": "status", "value" : "1", "operator": "="}]`

HTTP Response: 200 Success

## Get A User-Score Entry

`GET /api/user_score/#{user_score_id}`

HTTP Response: 200 Success


## Create A New User-Score Entry

`POST /api/user_score`

HTTP Response: 201 Created

You need to post the following:

```json
{
    "user_id": 1,
    "date": "2014-05-17",
    "score": 55,
    "percent": 77
}
```

## Update A User-Score Entry

`PUT /api/user_score/#{user_score_id}`

HTTP Response: 200 OK

You may update selected attributes for a task.

```json
{
    "score": 66,
    "percent": 83
}
```


## Archive A User-Score Entry

`PUT /api/user_score/#{user_score_id}`

```json
{
    "status": "0"
}
```
HTTP Response: 200 OK


## Delete A User-Score Entry

`DELETE /api/user_score/#{user_score_id}`

HTTP Response: 200 OK


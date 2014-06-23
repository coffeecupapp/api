# Projects

## Get All Projects

`GET /api/project`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/project
```

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "5",
    "project" : [
      {
        "id": 1,
        "name": "Projekt 1",
        "bill_by": 0, // 0: not billable, 1: client hourly rate, 2: project hourly rate, 3: user hourly rate, 4: task hourly rate
        "budget_by": 0, // 0: no budget, 1: total project hours, 2: total project amount, 3: budget per user, 4: budget per task 
        "comment": "",
        "internal": false,
        "code": "PR1",
        "hourly_rate": "90.0000", // default null, only if bill_by = 2
        "budget": "900000.0000", // default null, only if budget_by = 2
        "budget_hours": "120.00", // default null, only if budget_by = 1
        "created": "0000-00-00 00:00:00",
        "modified": "2014-04-15 15:13:22",
        "status": 1,
        "client_id" : 1,
        "client" : {
          "id" : 1,
          "currency_id" : 1,
          "created" : "0000-00-00 00:00:00",
          "modified" : "0000-00-00 00:00:00",
          "name" : "Client 1"
        },
        "color_id": 1,
        "color": {
          "id": 1,
          "label": "red",
          "hex": "ff0000",
          "created": "2014-04-08 15:12:51",
          "modified": "2014-04-08 15:12:51"
        },
        "user_assignments": [
            {
                "id": 1,
                "project_id": 1,
                "user_id": 1,
                "project_manager": false,
                "hourly_rate": "", // default null, only if bill_by = 3
                "budget": "", // default null, only if budget_by = 3
                "modified": "0000-00-00 00:00:00",
                "created": "0000-00-00 00:00:00",
                "status": 1
            },
            {
                ...
            }
        ],
        "task_assignments": [
            {
                "id": 1,
                "project_id": 1,
                "task_id": 1,
                "billable": true,
                "hourly_rate": "", // default null, only if bill_by = 4
                "budget": "", // default null, only if budget_by = 4
                "created": "0000-00-00 00:00:00",
                "modified": "0000-00-00 00:00:00",
                "status": 1
            },
            {
                ...
            }
        ]
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

## Get Archived Projects Only

`GET /api/project?filter=[{"property": "status", "value" : "0", "operator": "="}]`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Projects (DEFAULT Behaviour)

`GET /api/project?filter=[{"property": "status", "value" : "0", "operator": ">="}]`

HTTP Response: 200 Success

## Get Non-Archived Projects Only

`GET /api/project?filter=[{"property": "status", "value" : "1", "operator": "="}]`

HTTP Response: 200 Success

## Get A Single Project

`GET /api/project/#{project_id}`

HTTP Response: 200 Success


## Create A New Project

`POST /api/project`

HTTP Response: 201 Created

You need to post the following:

```json
{
        "color_id": 1,
        "client_id": 1,
        "name": "Project XY",
        "comment": "foo",
        "code": "PXY",
        ...
}
```

## Update A Project

`PUT /api/project/#{project_id}`

HTTP Response: 200 OK

You may update selected attributes for a project.

```json
{
    "name": "Project new Name"
}
```

## Archive A Project

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE ENTRY, IF ANY

`PUT /api/project/#{project_id}`

```json
{
    "status": "0"
}
```
HTTP Response: 200 OK

## Delete A Project

`DELETE /api/project/#{project_id}`

If project does not have associated time entries or expenses CoffeeCup deletes it and returns
HTTP Response: 200 OK

otherwise project is not deleted and you'll get a HTTP Response: 500 Could not delete model.

```json
{
    "success": false,
    "message": "Could not delete model",
    "data": {
        "errorCode": 500,
        "message": "Could not delete model"
    }
}
```


## Get All Tasks Of A Project

`GET /api/project/1/tasks`

## Get All Users Of A Project

`GET /api/project/1/users`

## Get user 3 who is on project 1
or simply checking whether user 3 is on that project

`GET /api/project/1/users/3`

## Get user 3 who is also on project 3

`GET /api/project/3/users/3`

## Add user 3 also to project 2

`PUT /api/project/2/users/3`

## Get all projects of user 3

`GET /api/user/3/projects`

## Remove user 3 from project 1 (but NOT delete the user itself)

`DELETE /api/project/1/users/3`


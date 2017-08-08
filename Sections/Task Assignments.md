# Task Assignmets

## Constants for enum fields

### status

- `0` - TaskAssignment archived
- `1` - TaskAssignment active


## Get All TaskAssignments

`GET /v1/taskAssignments`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/taskAssignments
```

HTTP Response: 200 Success

```json
{
  "taskAssignments": [
    {
      "status": 0,
      "billable": true,
      "hourlyRate": 100,
      "budgetHours": 0,
      "task": 442,
      "project": 1005,
      "id": 5384
    },
    {
      "status": 1,
      "billable": true,
      "hourlyRate": 100,
      "budgetHours": null,
      "task": 441,
      "project": 1006,
      "id": 5385
    },
    /* ... */
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 11,
    "criteria": {}
  }
}
```

## Get Archived TaskAssignments Only

`GET /v1/taskAssignments?status[]=0`

HTTP Response: 200 Success

## Get Archived AND Non-Archived TaskAssignments (DEFAULT Behaviour)

`GET /v1/taskAssignments?status[]=0&status[]=1`

HTTP Response: 200 Success

## Get Non-Archived TaskAssignments Only

`GET /v1/taskAssignments?status[]=1`

HTTP Response: 200 Success

## Get A TaskAssignments

`GET /v1/taskAssignments/#{taskAssignment_id}`

HTTP Response: 200 Success

## Get TaskAssignments for specific Projects

`GET /v1/taskAssignments?project[]=1005&project[]=1006`

HTTP Response: 200 Success

## Get TaskAssignments for specific Tasks 

`GET /v1/taskAssignments?task[]=441&task[]=442`

HTTP Response: 200 Success


## Create A New TaskAssignments

`POST /v1/taskAssignments`

HTTP Response: 201 Created

You need to post the following:

```json
{
  "taskAssignment": {
    "task": 443,
    "project": 1005,
    "billable": true,
    "hourlyRate": 100,
    "budgetHours": null
  }
}
```

## Update A TaskAssignments

`PUT /v1/taskAssignments/#{taskAssignment_id}`

HTTP Response: 200 OK

You may update selected attributes for a task assignment.

```json
{
  "taskAssignment": {
    "billable": true
  }
}
```


## Archive A Task Assignment 

Archiving a task assignment cascades to all time entries associated that are associated to both the task and project.

`PUT /v1/taskAssignments/#{taskAssignment_id}`

```json
{
  "taskAssignment": {
    "status": 0
  }
}
```
HTTP Response: 200 OK


## Delete A TaskAssignments

`DELETE /v1/taskAssignments/#{taskAssignment_id}`

If the project does not have time entries associated with this task CoffeeCup deletes it and returns
HTTP Response: 200 OK

otherwise task is not deleted and you'll get a HTTP Response: 500 Could not delete model.

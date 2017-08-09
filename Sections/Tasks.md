# Tasks

## Constants for enum fields

### status

- `0` - Task archived
- `1` - Task active


## Get All Tasks

`GET /v1/tasks`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/tasks
```

HTTP Response: 200 Success

```json
{
  "tasks": [
    {
      "status": 1,
      "label": "Coding",
      "code": "cdng",
      "hourlyRate": 90,
      "favorite": true,
      "billable": true, // default value, can be overridden by TaskAssignemnt
      "color": 11,
      "id": 1
    },
    {
      "status": 1,
      "label": "Design",
      "code": "dsgn",
      "hourlyRate": 333,
      "favorite": true,
      "billable": true,
      "color": 11,
      "id": 2
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

## Get Archived Tasks Only

`GET /v1/tasks?status[]=0`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Tasks (DEFAULT Behaviour)

`GET /v1/tasks?status[]=0&status[]=1`

HTTP Response: 200 Success

## Get Non-Archived Tasks Only

`GET /v1/tasks?status[]=1`

HTTP Response: 200 Success

## Get A Task

`GET /v1/tasks/#{task_id}`

HTTP Response: 200 Success


## Create A New Task

`POST /v1/tasks`

HTTP Response: 201 Created

You need to post the following:

```json
{
  "task": {
    "label": "Icons designen"
  }
}
```

## Update A Task

`PUT /v1/tasks/#{task_id}`

HTTP Response: 200 OK

You may update selected attributes for a task.

```json
{
  "task": {
    "favorite": true
  }
}
```


## Archive A Task

**Archiving a task cascades to task assignments associated to it** (see [Task Assignments Section](Task%20Assignments.md))
You can't assign archived tasks to projects.

`PUT /v1/tasks/#{task_id}`

```json
{
  "task": {
    "status": 0
  }
}
```
HTTP Response: 200 OK


## Delete A Task

`DELETE /v1/tasks/#{task_id}`

If task does not have associated time entries CoffeeCup deletes it and returns
HTTP Response: 200 OK

otherwise task is not deleted and you'll get a HTTP Response: 500 Could not delete model.

## Assignments to Projects

Assignments to projects are managed through [Task Assignments](Task%20Assignments.md).

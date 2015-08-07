# Tasks

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
      "billable": true,
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

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE TASK ENTRY?

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


## Get All Projects that are allowed to track time using this task

`GET /v1/taskAssignments?task[]=1`

For project-IDs 1, 3 and 37:

`GET /v1/projects?id[]=1&id[]=3&id[]=37`

HTTP Response: 200 Success

## To allow time tracking of task 3 in project 2, use

```
PUSH /v1/taskAssignments

{
  "taskAssignment": {
    "task": 3,
    "project":2
  }
}
```

## To prevent a certain task 2 to be used within a project 3, use

`GET /v1/taskAssignments?task[]=2&project[]=3`

With the returned ID:

`DELETE /v1/taskAssignments/#{id}`



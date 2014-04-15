# Tasks

## Get All Tasks

`GET /api/task`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/task
```

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "11",
    "task" : [
      {
        "category" : {
          "id" : 1,
          "created" : "0000-00-00 00:00:00",
          "label" : "task cat 1",
          "modified" : "0000-00-00 00:00:00"
        },
        "id" : 1,
        "hourly_rate" : "90.9900",
        "category_id" : 1,
        "color_id": 1,
        "created" : "2014-02-08 22:35:00",
        "label" : "code",
        "billable_default" : true,
        "modified" : "2014-02-08 22:35:00",
        "projects" : [
          {
            "id" : 1,
            "color_id": 1,
            "client_id" : 1,
            "invoice_type_index" : 0,
            "budget_type_index" : 0,
            "budget" : "900000.0000",
            "code" : "PR1",
            "hourly_rate" : "90.0000",
            "created" : "0000-00-00 00:00:00",
            "modified" : "0000-00-00 00:00:00",
            "comment" : "",
            "name" : "Projekt 1"
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

## Get A Task

`GET /api/task/#{task_id}`

HTTP Response: 200 Success


## Create A New Task

`POST /api/task`

HTTP Response: 201 Created

You need to post the following:

```json

{
    "hourly_rate" : "90",
    "category_id" : 1,
    "color_id": 1,
    "label" : "design",
    "billable_default" : 1
}
```

## Update A Task

`PUT /api/task/#{task_id}`

HTTP Response: 200 OK

You may update selected attributes for a task.

```json
{
    "label": "Tasks new Name",
    "billable_default" : 0
}

```

## Delete A Task

`DELETE /api/task/#{task_id}`

If task does not have associated time entries CoffeeCup deletes it and returns HTTP Response: 200 OK otherwise task is not deleted and you'll get a HTTP Response: 400 Bad Request .


## Get All Projects that are allowed to track time using this task

`GET /api/task/1/projects`

## To allow time tracking of task 3 in project 2, use

`PUT /api/project/2/tasks/3`

## To prevent a certain task 2 to be used within a project 3, use

`DELETE /api/project/3/task/2`


# Task Categories

## Get All Task Categories

`GET /api/task_category`

Example request

```shell
curl -v -u admin:admin  \
	-H "Content-type: application/json" \
	-X GET http://dev.coffeecupapp.com/api/task_category
```

HTTP Response: 200 Success

```json
{
  "data" : {
    "totalCount" : "1",
    "task_category" : [
      {
        "id" : 1,
        "created" : "0000-00-00 00:00:00",
        "label" : "task cat 1",
        "modified" : "0000-00-00 00:00:00"
      }
    ]
  },
  "success" : true,
  "message" : "Record(s) Found"
}
```

## Create A Task Category

`POST /api/task_category`

HTTP Response: 201 Created

You need to post the following:

```json
{
    "label" : "task cat 2",
}
```

## Update A Task Category

`PUT /api/task_category/#{task_category_id}`

HTTP Response: 200 OK

You may update selected attributes for a client.

```json
{
    "label" : "task new catname",
}
```

## Delete A Task Category

`DELETE /api/task_category/#{task_category_id}`
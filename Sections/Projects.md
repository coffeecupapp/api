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
        "id" : 1,
        "modified" : "0000-00-00 00:00:00",
        "users" : [
          {
            "id" : 1,
            "type_index" : 0,
            "date_format" : "d.m.Y",
            "beginning_of_week" : 0,
            "modified" : "2014-02-08 17:12:19",
            "lastname" : "nachname",
            "last_active_at" : "0000-00-00 00:00:00",
            "hourly_rate" : "90.9900",
            "image_url" : "",
            "firstname" : "vorname",
            "timeofday_format" : "H:i:s",
            "language" : "de_DE",
            "created" : "2014-02-08 17:12:19",
            "timezone" : "Europe/Berlin",
            "role_index" : 0,
            "last_login_at" : "0000-00-00 00:00:00",
            "email" : "1@2gu.de"
          },
          {
            ...
          }
        ],
        "tasks" : [
          {
            "id" : 1,
            "hourly_rate" : "90.9900",
            "category_id" : 1,
            "color_id": 1,
            "created" : "2014-02-08 22:35:00",
            "label" : "code",
            "billable_default" : 1,
            "modified" : "2014-02-08 22:35:00"
          },
          {
            ...
          }
        ],
        "hourly_rate" : "90.0000",
        "invoice_type_index" : 0,
        "comment" : "",
        "code" : "PR1",
        "budget" : "900000.0000",
        "created" : "0000-00-00 00:00:00",
        "client_id" : 1,
        "client" : {
          "id" : 1,
          "currency_id" : 1,
          "created" : "0000-00-00 00:00:00",
          "modified" : "0000-00-00 00:00:00",
          "name" : "Client 1"
        },
        "budget_type_index" : 0,
        "name" : "Projekt 1",
        "color_id": 1,
        "color": {
          "id": 1,
          "label": "red",
          "hex": "ff0000",
          "created": "2014-04-08 15:12:51",
          "modified": "2014-04-08 15:12:51"
        },
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

## Get A Project

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

## Delete A Project

`DELETE /api/project/#{project_id}`

If project does not have associated invoices CoffeeCup deletes it and returns HTTP Response: 200 OK otherwise project is not deleted and you'll get a HTTP Response: 400 Bad Request .


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


# Projects

## Get All Projects

`GET /v1/projects`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/projects
```
HTTP Response: 200 Success

```json
{
  "projects": [
    {
      "client": 1,
      "color": 1,
      "status": 1,
      "name": "Projekt 1",
      "comment": "gutes Projekt",
      "code": "PR1",
      "billBy": 2,
      "budgetBy": 2,
      "hourlyRate": 90,
      "budget": 1267.89,
      "budgetHours": 0,
      "id": 1
    },
    {
      "client": 2,
      "color": 2,
      "status": 1,
      "name": "Projekt 2",
      "comment": "schönes Projekt",
      "code": "PR2",
      "billBy": 0,
      "budgetBy": 0,
      "hourlyRate": 90,
      "budget": 10000,
      "budgetHours": 0,
      "id": 2
    },
    /* ... */
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 8,
    "criteria": {}
  }
}
```

## Get Archived Projects Only

`GET /v1/projects?status[]=0`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Projects (DEFAULT Behaviour)

`GET /v1/projects?status[]=0&status[]=1`

HTTP Response: 200 Success

## Get Non-Archived Projects Only

`GET /v1/projects?status[]=1`

HTTP Response: 200 Success

## Get A Single Project

`GET /v1/projects/#{project_id}`

HTTP Response: 200 Success


## Create A New Project

`POST /v1/projects`

HTTP Response: 201 Created

You need to post the following:

```json
{
  "project": {
    "name": "Motor X1337"
  }
}
```

## Update A Project

`PUT /v1/projects/#{project_id}`

HTTP Response: 200 OK

You may update selected attributes for a project.

```json
{
  "project": {
    "name": "Motor X1337 v2"
  }
}
```

## Archive A Project

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE ENTRY, IF ANY

`PUT /v1/projects/#{project_id}`

```json
{
  "project": {
    "status": 0
  }
}
```
HTTP Response: 200 OK

## Delete A Project

`DELETE /v1/projects/#{project_id}`

If project does not have associated time entries or expenses CoffeeCup deletes it and returns
HTTP Response: 200 OK

otherwise project is not deleted and you'll get a HTTP Response: 500 Could not delete model.


## Get All Tasks Of A Project

`GET /v1/taskAssignments?project[]=1`

For task-IDs 1, 3 and 37:

`GET /v1/tasks?id[]=1&id[]=3&id[]=37`

HTTP Response: 200 Success

## Get All Users Of A Project

`GET /v1/userAssignments?project[]=1`

For user-IDs 1, 3 and 37:

`GET /v1/users?id[]=1&id[]=3&id[]=37`

HTTP Response: 200 Success

## Get user 3 who is on project 1
or simply checking whether user 3 is on that project

`GET /v1/userAssignments?user[]=3&project[]=1`

## Get user 3 who is also on project 3

`GET /v1/userAssignments?user[]=3&project[]=3`

## Add user 3 also to project 2

```
PUSH /v1/userAssignments

{
  "userAssignment": {
    "user": 3,
    "project":2
  }
}
```

## Get all projects of user 3

`GET /v1/userAssignments?user[]=1`

For project-IDs 1, 3 and 37:

`GET /v1/projects?id[]=1&id[]=3&id[]=37`

## Remove user 3 from project 1 (but NOT delete the user itself)

`GET /v1/userAssignments?user[]=3&project[]=1`

With the returned ID:

`DELETE /v1/userAssignments/#{id}`


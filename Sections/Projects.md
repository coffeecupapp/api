# Projects

## Constants for enum fields

### status

- `0` - Project archived
- `1` - Project active

### budgetBy

- `0` - No Budget, billing by effort
- `1` - Budget based on total hours spend (`budgetHours` field)
- `2` - Budget based on total amount spent (`budget` field)
- `3` - Budget per user assigned to this project (see [User Assignments section](User%20Assignments.md))
- `4` - Budget per task assigned to this project (see [Task Assignemnts section](Task%20Assignments.md))

### billBy

- `0` - Do not apply an hourly rate for billing
- `1` - Bill by the hourly rate set on the client (see [Clients section](Clients.md))
- `2` - Bill by the hourly rate set on the project (`hourlyRate` field)
- `3` - Bill by the hourly rate set per user assigned (see [User Assignments section](User%20Assignments.md))
- `4` - Bill by the hourly rate set per task assigned (see [Task Assignemnts section](Task%20Assignments.md))


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

**Archiving a project cascades to task and user assignments associated to it** (see [Task Assignments](Task%20Assignments.md) and [User Assignments](User%20Assignments.md) Sections)
You can't assign new tasks or users to archived projects.

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

## Assigning Users

User assignments are managed through [User Assignemnts](User%20Assignemnts.md). 

## Assigning Tasks

Task assignments are managed through [Task Assignemnts](Task%20Assignemnts.md).

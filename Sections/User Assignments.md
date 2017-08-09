# User Assignments

## Constants for enum fields

### status

- `0` - UserAssignment archived
- `1` - UserAssignment active


## Get All UserAssignments

`GET /v1/userAssignments`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/userAssignments
```

HTTP Response: 200 Success

```json
{
  "userAssignments": [
    {
      "status": 1,
      "hourlyRate": 100,
      "budgetHours": null,
      "user": 335,
      "project": 1005,
      "isProjectManager": true,
      "id": 2824
    },
    {
      "status": 0,
      "hourlyRate": null,
      "budgetHours": null,
      "user": 335,
      "project": 1006,
      "isProjectManager": true,
      "id": 2825
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

## Get Archived UserAssignments Only

`GET /v1/userAssignments?status[]=0`

HTTP Response: 200 Success

## Get Archived AND Non-Archived UserAssignments (DEFAULT Behaviour)

`GET /v1/userAssignments?status[]=0&status[]=1`

HTTP Response: 200 Success

## Get Non-Archived UserAssignments Only

`GET /v1/userAssignments?status[]=1`

HTTP Response: 200 Success

## Get A UserAssignments

`GET /v1/userAssignments/#{userAssignment_id}`

HTTP Response: 200 Success

## Get UserAssignments for specific Projects

`GET /v1/userAssignments?project[]=1005&project[]=1006`

HTTP Response: 200 Success

## Get UserAssignments for specific Users 

`GET /v1/userAssignments?user[]=335&user[]=336`

HTTP Response: 200 Success


## Create A New UserAssignments

`POST /v1/userAssignments`

HTTP Response: 201 Created

You need to post the following:

```json
{
  "userAssignment": {
      "hourlyRate": null,
      "budgetHours": null,
      "user": 335,
      "project": 1006,
      "isProjectManager": true
  }
}
```

## Update A UserAssignments

`PUT /v1/userAssignments/#{userAssignment_id}`

HTTP Response: 200 OK

You may update selected attributes for a user assignment.

```json
{
  "userAssignment": {
    "isProjectManager": false 
  }
}
```


## Archive A User Assignment 

**Archiving a user assignment cascades to time entries that are associated to both this project and user** (see [Time Tracking Section](Time%20Tracking.md))
You can't create new or edit existing entries for archived user assignments.

`PUT /v1/userAssignments/#{userAssignment_id}`

```json
{
  "userAssignment": {
    "status": 0
  }
}
```
HTTP Response: 200 OK


## Delete A UserAssignments

`DELETE /v1/userAssignments/#{userAssignment_id}`

If the project does not have time entries associated with this user CoffeeCup deletes it and returns
HTTP Response: 200 OK

otherwise user is not deleted and you'll get a HTTP Response: 500 Could not delete model.

# CAUTION: MIGHT BE OUT OF DATE

# Time Tracking

The Time tracking API allows you to access and manipulate time entries in similar fashion to using the daily timesheet view. 
This allows developers to create lightweight clients or widgets to track time beyond directly interacting with CoffeeCup through the web browser.

# Time Entries

## Get All Time Entries

`GET /v1/timeEntries`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/timeEntries
```

HTTP Response: 200 Success

```json
{
  "timeEntries": [
    {
      "task": 3,
      "project": 2,
      "user": 2,
      "status": 1,
      "day": "2014-02-08",
      "starttime": "14:49:00",
      "endtime": "15:34:00",
      "duration": 2700,
      "running": false,
      "comment": "Reifen tauschen",
      "id": 14
    },
    {
      "task": 4,
      "project": 2,
      "user": 2,
      "status": 1,
      "day": "2014-02-08",
      "starttime": "14:49:00",
      "endtime": "15:34:00",
      "duration": 2700,
      "running": false,
      "comment": "Rot streichen",
      "id": 15
    },
    /* ... */
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 545,
    "criteria": {}
  }
}
```

## Get Archived Time Entries Only

`GET /v1/timeEntries?status[]=0`

HTTP Response: 200 Success

## Get Archived AND Non-Archived Time Entries (DEFAULT Behaviour)

`GET /v1/timeEntries?status[]=0&status[]=1`

HTTP Response: 200 Success

## Get Non-Archived Time Entries Only

`GET /v1/timeEntries?status[]=1`

HTTP Response: 200 Success

## Get time entries by project ##
To show only the time_entries of a certain project, pass the GET Params (URL encoded).

`GET /v1/timeEntries?project[]=1`

HTTP Response: 200 Success

## Get time entries by user ##
To show only the time_entries of a certain user, pass the GET Params (URL encoded).

`GET /v1/timeEntries?user[]=1`

HTTP Response: 200 Success

## Get time entries by user AND project ##
To show the time_entries of a certain user and project, combine the above (URL encoded).

`GET /v1/timeEntries?user[]=1project[]=1`

HTTP Response: 200 Success

## Get time entries by Date ##
To show only the time_entries that have a time after "2013-01-01 17:23", pass the UTC date value (URL encoded).

`GET /v1/timeentries?where={"day":{">=": "2013-01-01"}}`

HTTP Response: 200 Success

## Get time entries For A Given Timeframe ##
To show only the time_entries that have a time between "2013-01-01" and "2015-01-31" (UTC), pass these values (URL encoded).

`GET /v1/timeentries?where={"day":{">=": "2013-01-01", "<=": "2015-01-31"}}`

HTTP Response: 200 Success

## Create a new time entry ##

`POST /v1/timeEntries`

HTTP Response: 201 Created

You may post the following

```json
{
  "timeEntry": {
    "user": 1,
    "task": 1,
    "project": 1,
    "comment": "repo aufsetzen"
  }
}
```

## Update a time entry ##

`PUT /v1/timeEntries/{time_entry_id}`

HTTP Response: 200 OK

You may update selected attributes for a client.

```json
{
  "timeEntry": {
    "comment": "git repo aufsetzen"
  }
}
```
"budgetHours": 0,
## Create a running time entry ##

`POST /v1/timeEntries`

HTTP Response: 200 OK

```json
{
  "timeEntry": {
    "user": 1,
    "task": 1,
    "project": 1,
    "comment": "repo aufsetzen",
    "running": true
  }
}
```

## STOP/PAUSE a running time entry ##

`PUT /v1/timeEntries/{time_entry_id}`

```json
{
  "timeEntry": {
    "running": false
  }
}
```

Will return the duration in seconds since you started working on it (running:true) 

HTTP Response: 200 Success

```json
{
  "timeEntry": {
    "task": 1,
    "project": 1,
    "user": 1,
    "status": 1,
    "day": null,
    "starttime": null,
    "endtime": null,
    "duration": 1337,
    "running": false,
    "comment": "git repo aufsetzen",
    "id": 597
  }
}
```

## STOP/PAUSE a running time entry and manually set the duration ##

`PUT /v1/timeEntries/{time_entry_id}`

```json
{
  "timeEntry": {
    "running": false,
    "duration": 1000
  }
}
```

Will override the duration since you started working on it 

HTTP Response: 200 Success

## Delete a time entry ##

`DELETE /v1/timeEntries/{time_entry_id}`

HTTP Response: 200 Success

## Archive A Time Entry

### TODO: DOKU WHAT WILL BE ARCHIVED ALONG WITH THE ENTRY, IF ANY

`PUT /v1/timeEntries/{time_entry_id}`

```json
{
  "timeEntry": {
    "status": 0
  }
}
```
HTTP Response: 200 OK




# User Employment 

## Constants for enum fields

### employmentType

`0` - Employee
`1` - Freelancer
`2` - Former Employee

## Get All UserEmployments for specific User

`GET /v1/userEmployments?user=337`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/userEmployments?user=337
```

HTTP Response: 200 Success

```json
{
  "userEmployments": [
    {
      "user": 337,
      "employmentType": 0,
      "validFrom": "2017-08-03",
      "employerContribution": 0,
      "monthlyRemuneration": 0,
      "hourlyRemuneration": null,
      "workHoursType": 0,
      "hoursWeekly": null,
      "hoursMonday": 8,
      "hoursTuesday": 8,
      "hoursWednesday": 8,
      "hoursThursday": 8,
      "hoursFriday": 8,
      "hoursSaturday": 0,
      "hoursSunday": 0,
      "id": 2
    },
    {
      "user": 337,
      "employmentType": 0,
      "validFrom": "2017-08-08",
      "employerContribution": 0,
      "monthlyRemuneration": 0,
      "hourlyRemuneration": null,
      "workHoursType": 0,
      "hoursWeekly": null,
      "hoursMonday": 8,
      "hoursTuesday": 8,
      "hoursWednesday": 8,
      "hoursThursday": 8,
      "hoursFriday": 8,
      "hoursSaturday": 0,
      "hoursSunday": 0,
      "id": 3
    }    /* ... */
  ],
  "meta": {
    "skip": 0,
    "limit": 30,
    "total": 11,
    "criteria": {}
  }
}
```

## Get A UserEmployment

`GET /v1/userEmployments/#{userEmployment_id}`

HTTP Response: 200 Success


## Create A New UserEmployments

`POST /v1/userEmployments`

HTTP Response: 201 Created

You need to post the following:

```json
{
  "userEmployment": {
      "user": 337,
      "employmentType": 0,
      "validFrom": "2017-12-25",
      "employerContribution": 0,
      "monthlyRemuneration": 0,
      "hourlyRemuneration": null,
      "workHoursType": 0,
      "hoursWeekly": null,
      "hoursMonday": 8,
      "hoursTuesday": 8,
      "hoursWednesday": 8,
      "hoursThursday": 8,
      "hoursFriday": 8,
      "hoursSaturday": 0,
      "hoursSunday": 0,
  }
}
```

## Update A UserEmployments

`PUT /v1/userEmployments/#{userEmployment_id}`

HTTP Response: 200 OK

You may update selected attributes for a user employment.

```json
{
  "userEmployment": {
    "employmentType": 1
  }
}
```



## Delete A UserEmployments

`DELETE /v1/userEmployments/#{userEmployment_id}`

HTTP Response: 200 OK

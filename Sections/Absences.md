# Absences

## Constants for enum fields

### rangeType

- `MULTIPLE_DAYS_FULL` - A whole day or more
- `ONE_DAY_HALF` - Counts half a day

## Boolean Fields

- `countsAsVacation` - Reduces the vacation budget (READONLY, determined by `absenceType`)
- `workHoursExpected` - Employee has to work (READONLY, determined by `absenceType`)
- `remunerationActive` - Is remuneration active (READONLY, determined by `absenceType`)
- `reducesOvertime` - Reduces the overtime of an employee (READONLY, determined by `absenceType`)

## Foreign Keys

- `user` - (see [User section](Users.md))
- `absenceType` - (see [Absence Type section](Absence%20Types.md))

## Get All Absences

`GET /v1/absences`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/absences
```
HTTP Response: 200 Success

```json
{
  "absences": [
    {
      "createdAt": "2017-01-17T16:07:11.000Z",
      "updatedAt": "2017-01-14T09:34:46.000Z",
      "id": 1,
      "rangeType": "MULTIPLE_DAYS_FULL",
      "startDate": "2017-01-26",
      "endDate": "2017-02-04",
      "comment": "sick",
      "countsAsVacation": false,
      "workHoursExpected": false,
      "remunerationActive": true,
      "reducesOvertime": false,
      "user": 1,
      "absenceType": 1
    },
    {
      "createdAt": "2017-02-24T16:27:02.000Z",
      "updatedAt": "2017-02-24T16:27:02.000Z",
      "id": 65,
      "rangeType": "MULTIPLE_DAYS_FULL",
      "startDate": "2017-02-26",
      "endDate": "2017-03-04",
      "comment": "Skiing",
      "countsAsVacation": true,
      "workHoursExpected": false,
      "remunerationActive": true,
      "reducesOvertime": false,
      "user": 1,
      "absenceType": 2
    }
  ],
  "meta": {
    "skip": 0,
    "limit": 10000,
    "total": 2,
    "sort": [],
    "criteria": {}
  }
}
```

## Create A New Absence

`POST /v1/absences`

HTTP Response: 201 Created

You need to post the following:

```json
{
  "absence": {
      "rangeType": "MULTIPLE_DAYS_FULL",
      "startDate": "2017-02-26",
      "endDate": "2017-03-04",
      "comment": null,
      "user": 1,
      "absenceType": 1
  }
}
```

## Update An Absence

`PUT /v1/absences/{id}`

HTTP Response: 200 OK

```json
{
  "absence": {
      "rangeType": "MULTIPLE_DAYS_FULL",
      "startDate": "2017-02-26",
      "endDate": "2017-03-04",
      "comment": null,
      "user": 1,
      "absenceType": 1
  }
}
```

## Delete An Absence

`DELETE /v1/absences/{id}`

If the user is allowed to delete an absence it returns
HTTP Response: 200 OK


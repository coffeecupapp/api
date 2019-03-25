# Absence Types

## Constants for enum fields

### status

- `0` - Absence Type inactive
- `1` - Absence Type active

## Boolean Fields

- `canBeRequested` - Can be created as a request by an employee
- `detailsVisibleToOtherUsers` - Is visible for other employees
- `defaultCountsAsVacation` - Reduces the vacation budget
- `defaultWorkHoursExpected` - Employee has to work
- `defaultRemunerationActive` - Is remuneration active
- `defaultReducesOvertime` - Reduces the overtime of an employee

## Get All Absence Types

`GET /v1/absencetypes`

Example request

```shell
curl \
  -H "Authorization: Bearer 14df41535ce02fd3f69a53ab80184a691337f80a" \
  -X GET https://api.coffeecupapp.com/v1/absencetypes
```
HTTP Response: 200 Success

```json
{
  "absenceTypes": [
    {
      "createdAt": "2018-07-27T17:38:26.000Z",
      "updatedAt": "2018-07-27T17:38:26.000Z",
      "id": 1,
      "status": 1,
      "label": "Vacation",
      "color": 1,
      "icon": 1,
      "canBeRequested": true,
      "detailsVisibleToOtherUsers": true,
      "defaultCountsAsVacation": true,
      "defaultWorkHoursExpected": false,
      "defaultRemunerationActive": true,
      "defaultReducesOvertime": false
    },
    {
      "createdAt": "2018-07-27T17:38:26.000Z",
      "updatedAt": "2018-10-24T15:36:27.000Z",
      "id": 2,
      "status": 1,
      "label": "Sickness",
      "color": 2,
      "icon": 2,
      "canBeRequested": false,
      "detailsVisibleToOtherUsers": true,
      "defaultCountsAsVacation": false,
      "defaultWorkHoursExpected": false,
      "defaultRemunerationActive": true,
      "defaultReducesOvertime": false
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

## Create A New Absence Type

`POST /v1/absencetypes`

HTTP Response: 201 Created

You need to post the following:

```json
{
  "absenceType": {
    "label": "New Abwesence Type",
    "color": 8,
    "icon": 3,
    "status": 1,
    "canBeRequested": false,
    "defaultCountsAsVacation": false,
    "defaultWorkHoursExpected": false,
    "detailsVisibleToOtherUsers": false,
    "defaultRemunerationActive": false,
    "defaultReducesOvertime": false
  }
}
```

## Update An Absence Type

`PUT /v1/absencetypes/{id}`

HTTP Response: 200 OK

Only changes to the label, the icon and the color affect existing absences. All further changes to the settings only affect absences created in the future.

```json
{
  "absenceType": {
    "label": "New Label"
  }
}
```

## Delete An Absence Type

Absence Types cannot be deleted. Instead please set the status to 0 for hiding it in clients.



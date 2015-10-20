# Analytics

## Project


`GET /v1/analytics/projects`


###Multiple project analytics (sparse list):

`GET /v1/analytics/projects`
`GET /v1/analytics/projects?project[]=`**`PROJECT_ID`**`project[]=`**`PROJECT_ID`**

HTTP Response: 200 Success

```json
{
  "analyticsProjects": [
    {
      "id": 78,
      "project": 78,
      "hours": {
        "spent": 75487.13638888889,
        "billable": 60239.938888888886,
        "nonBillable": 15247.1975,
        "budget": null,
        "outOfBudget": null
      },
      "amount": {
        "billable": 180719.2486,
        "budget": null,
        "outOfBudget": null
      }
    }
    /* ... */
  ]
}
```

###Single project analytics (detailed):

`GET /v1/analytics/projects?project=`**`PROJECT_ID`**

HTTP Response: 200 Success

```json
{
  "analyticsProject": {
    "id": 105,
    "project": 105,
    "hours": {
      "spent": 59364.35833333333,
      "billable": 44251.56972222222,
      "nonBillable": 15112.788611111111,
      "budget": null,
      "outOfBudget": null
    },
    "amount": {
      "billable": 4425156.4622,
      "budget": 700,
      "outOfBudget": 4424456.4622
    },
    "monthlyHistogram": [
      {
        "date": "2013-03-01T00:00:00.000Z",
        "timestamp": 1362096000000,
        "hours": {
          "spent": 984.6122222222223,
          "billable": 753.7183333333334,
          "nonBillable": 230.89388888888888
        },
        "amount": {
          "billable": 75371.8253
        }
      }
      /* ... */
    ],
    "users": [
      {
        "id": 3,
        "hours": {
          "billable": 2.52,
          "nonBillable": 0,
          "spent": 2.52
        },
        "amount": {
          "billable": 252
        }
      }
      /* ... */
    ],
    "tasks": [
      {
        "id": 1,
        "hours": {
          "billable": 15028.670555555556,
          "nonBillable": 0,
          "spent": 15028.670555555556,
          "budget": 1,
          "outOfBudget": 15027.670555555556
        },
        "amount": {
          "billable": 1502866.8831,
          "budget": 100,
          "outOfBudget": 1502766.8831
        }
      }
      /* ... */
    ]
  }
}
```
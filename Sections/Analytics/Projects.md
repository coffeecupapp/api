# Project Analytics


`GET /v1/analytics/projects`

##Multiple project analytics (sparse list):

<code>
GET /v1/analytics/projects
</code>
<code>
GET /v1/analytics/projects?project[]=<b>PROJECT_ID</b>&project[]=<b>PROJECT_ID</b>
</code>

HTTP Response: 200 Success

```json
{
  "analyticsProjects": [
    {
      "id": 78,
      "project": 78,
      "hours": {
        "total": 75487.13638888889,
        "spent": 60239.938888888886,
        "nonBillable": 15247.1975,
        "budget": null,
        "outOfBudget": null,
        "billed": 0
      },
      "amount": {
        "spent": 180719.2486,
        "budget": null,
        "outOfBudget": null,
        "billed": 0
      }
    }
    /* ... */
  ]
}
```

##Single project analytics (detailed):

<code>
GET /v1/analytics/projects?project=<b>PROJECT_ID</b>
</code>

HTTP Response: 200 Success

```json
{
  "analyticsProject": {
    "id": 105,
    "project": 105,
    "hours": {
      "total": 59364.35833333333,
      "spent": 44251.56972222222,
      "nonBillable": 15112.788611111111,
      "budget": null,
      "outOfBudget": null,
      "billed": 0
    },
    "amount": {
      "spent": 4425156.4622,
      "budget": 700,
      "outOfBudget": 4424456.4622,
      "billed": 0
    },
    "monthlyHistogram": [
      {
        "date": "2013-03-01T00:00:00.000Z",
        "timestamp": 1362096000000,
        "hours": {
          "total": 984.6122222222223,
          "spent": 753.7183333333334,
          "nonBillable": 230.89388888888888
        },
        "amount": {
          "spent": 75371.8253
        }
      }    
      /* ... */
    ],
    "users": [
      {
        "id": 3,
        "hours": {
          "spent": 2.52,
          "nonBillable": 0,
          "total": 2.52
        },
        "amount": {
          "spent": 252
        }
      }
      /* ... */
    ],
    "tasks": [
      {
        "id": 1,
        "hours": {
          "spent": 15028.670555555556,
          "nonBillable": 0,
          "total": 15028.670555555556,
          "budget": 1,
          "outOfBudget": 15027.670555555556
        },
        "amount": {
          "spent": 1502866.8831,
          "budget": 100,
          "outOfBudget": 1502766.8831
        }
      }
      /* ... */
    ]
  }
}
```
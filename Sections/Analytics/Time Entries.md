# Time Entry Analytics


`GET /v1/analytics/time-entries`

<code>
GET /v1/analytics/time-entries?start_date=<b>START_DATE</b>&end_date=<b>END_DATE</b>
</code>

Optional (Users, Projects, Tasks, Project Clients):

<pre>
GET /v1/analytics/time-entries?start_date=<b>START_DATE</b>&end_date=<b>END_DATE</b>
  &user[]=<b>USER_1</b>&user[]=<b>USER_2</b>
  &project[]=<b>PROJECT_1</b>&project[]=<b>PROJECT_2</b>
  &task[]=<b>TASK_1</b>&task[]=<b>TASK_2</b>
  &project.client[]=<b>PROJECT_CLIENT_1</b>&project.client[]=<b>PROJECT_CLIENT_2</b>
</pre>

HTTP Response: 200 Success

```json
{
  "analyticsTimeEntries": {
    "startTimestamp": 1411855200000,
    "endTimestamp": 1475618399000,
    "hours": {
      "spent": 80249.81250000003,
      "billable": 67686.01055555558,
      "nonBillable": 12563.801944444444,
      "budget": 132,
      "outOfBudget": 24554.65027777778
    },
    "amount": {
      "billable": 2512944.1472000005,
      "budget": 700,
      "outOfBudget": 2439232.1522
    }
  }
}
```
